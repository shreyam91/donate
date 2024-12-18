# visit:- https://shreyam91.github.io/donate/

# Razorpay Payment Integration Project

This project demonstrates how to integrate **Razorpay**, a popular payment gateway, into a web application to enable secure online payments. By integrating Razorpay, users can make payments using various methods such as credit/debit cards, net banking, wallets, UPI, and more.

## Features

- **Seamless Payment Experience:** Users can make payments directly through the web interface.
- **Multiple Payment Options:** Supports cards, UPI, wallets, and net banking.
- **Payment Status Tracking:** The application tracks payment success/failure and updates the status accordingly.
- **Security:** Razorpay ensures high-level security with encrypted transactions.

## Technologies Used

- **Frontend:** HTML, CSS, JavaScript 
- **Backend:** Node.js
- **Payment Gateway:** Razorpay
  
## Prerequisites

Before you begin, ensure you have met the following requirements:

1. A **Razorpay Account**: If you don't have one, sign up on [Razorpay](https://razorpay.com/).
2. Node.js installed on your local machine (version 12.x or higher).
3. A code editor (e.g., VS Code).

## Installation

### 1. Clone the Repository

Clone this project to your local machine.

### 2. Install Dependencies

Install the required dependencies using npm.

```bash
npm install
```

### 3. Set Up Razorpay API Keys

To use Razorpay's API, you need the following:

- **Key ID**
- **Key Secret**

You can find these keys in your Razorpay dashboard. Set these keys in your project environment.

Create a `.env` file in the root of your project and add the following:

```
RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_key_secret
```

### 4. Configure Backend

Make sure your backend server is configured to handle payment requests. Typically, you'll need to:

- Generate an order via Razorpay API (`/createOrder`).
- Verify the payment signature on success (`/verifyPayment`).

### 5. Run the Application

Start the development server.

```bash
npm start
```

The server should now be running on `http://localhost:3000` (or another port if configured differently).

## Usage

### Frontend Workflow

1. **Initiate Payment**: The user selects a product/service and clicks on the 'Pay Now' button.
2. **Razorpay Checkout**: The frontend calls your backend, which triggers the Razorpay order creation. A unique order ID is generated, which is sent back to the frontend.
3. **Payment Popup**: Razorpay's Checkout.js popup appears, allowing the user to complete the payment.
4. **Payment Response**: Once the user completes the payment, Razorpay sends a payment response back to the frontend.
5. **Verify Payment**: The frontend sends the payment details to the backend to verify the payment signature.
6. **Payment Success/Failure**: Based on the verification response, the frontend shows a success or failure message.

### Backend Workflow

1. **Create Order**: When a user attempts to make a payment, the backend creates a Razorpay order using the Razorpay API.
2. **Verify Payment**: After receiving the payment response, the backend verifies the payment signature using Razorpay's official libraries to ensure the integrity and authenticity of the transaction.

## Testing

### Testing Payment Flow

You can use the **Razorpay Test Mode** and test your payment flows without real money transactions. Razorpay provides [test credentials](https://razorpay.com/docs/test-and-live/) and various [test cards](https://razorpay.com/docs/payment-gateway/test-card-details/) to simulate different payment scenarios.

### Sample Test Cards:

- Visa: `4111 1111 1111 1111`, Expiry: `12/22`, CVV: `123`
- Mastercard: `5555 5555 5555 4444`, Expiry: `12/22`, CVV: `123`

## Troubleshooting

- **Error 1:** `Signature verification failed!`
  - Ensure you're correctly passing the Razorpay order ID, payment ID, and signature for verification. Also, verify the `key_secret` and `key_id` in your `.env` file.
  
- **Error 2:** `Payment not successful.`
  - Check Razorpay's dashboard for transaction status and logs. Ensure you're using test cards in test mode.

## Contributing

If you'd like to contribute to this project, please fork the repository and submit a pull request with your changes. Feel free to report any issues or bugs you encounter.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
