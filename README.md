# URL Shortener Service (AWS Serverless)

## Overview
This project implements a simple URL shortener service using AWS serverless technologies.  
Users can submit a long URL, get a shortened URL, and be redirected to the original link via the short code.

---

## What the URL Shortener Does
- Takes a long URL input from the user  
- Generates a unique short code for the URL  
- Stores the mapping of short code to original URL in DynamoDB  
- Provides a short URL that redirects to the original URL  
- Handles URL redirection seamlessly via API Gateway and Lambda  
- Provides a simple frontend interface to create and access short URLs  

---

## Architecture
- **Frontend:** Static HTML + JavaScript page to input URLs and display shortened links  
- **Backend:** AWS Lambda function written in Node.js, handling URL shortening logic  
- **API:** AWS API Gateway exposing POST (create short URL) and GET (redirect) endpoints  
- **Database:** AWS DynamoDB table storing `shortCode` to `originalUrl` mappings  
- **Hosting:** Frontend hosted using AWS S3 static website hosting or AWS Amplify

---

## Features
- Generates unique 6-character short codes  
- Stores URL mappings in DynamoDB  
- Redirects users from short URL to original URL  
- Handles CORS for frontend API requests  
- Simple frontend with URL input and short URL display  

---

## Setup and Deployment

### DynamoDB
- Created a DynamoDB table named `UrlShortener`  
- Primary key: `shortCode` (String)  

### Lambda Function
- Runtime: Node.js 16.x or later  
- Handles POST and GET methods  
- Uses AWS SDK to interact with DynamoDB  
- Generates unique short codes  
- Configured environment variables:  
  - `TABLE_NAME = UrlShortener`  
  - `BASE_URL = https://{api-id}.execute-api.{region}.amazonaws.com/prod/`  

### API Gateway
- Created REST API with two methods:  
  - POST `/` → Lambda integration for URL shortening  
  - GET `/{shortCode}` → Lambda integration for redirection  
- Enabled Lambda proxy integration  
- Enabled CORS on both methods  

### Frontend
- Built a responsive, Bootstrap-based `index.html` with URL input and result display  
- Frontend calls API Gateway POST endpoint to create short URLs  
- Frontend hosted on AWS S3 static website hosting or AWS Amplify  

---

## Testing
- Used Postman and browser to test POST and GET API endpoints  
- Tested CORS and fixed via API Gateway configuration  
- Verified frontend works locally and deployed on AWS  

---

## Frontend Website
Access the live frontend here:  
[https://staging.d3r62xj5vom7vg.amplifyapp.com/](https://staging.d3r62xj5vom7vg.amplifyapp.com/)

![image](https://github.com/user-attachments/assets/6470003a-9ef0-4313-a802-e2e655707597)
![image](https://github.com/user-attachments/assets/095c1b86-9dcc-4fe1-8f00-42bf124d0191)

