# 🌩️ Vue 3 Portfolio on AWS S3 + CloudFront

## 🚀 Overview
This project demonstrates how to deploy a Vue 3 portfolio website using AWS S3 (for static hosting) and CloudFront (for global CDN with HTTPS).

## 🧰 Services Used
- Amazon S3
- Amazon CloudFront
- AWS IAM

## ⚙️ Deployment Steps
1. Build Vue app with `npm run build`
2. Upload `dist/` to S3 bucket
3. Enable static hosting
4. Create CloudFront distribution

## ⚙️ Setup Steps
1️⃣ Build your Vue 3 app

In your Vue project root directory:

```
yarn build
# or
npm run build
```

This will create a dist/ folder with static files ready to deploy.

2️⃣ Create and Configure an S3 Bucket

1. Go to AWS Console → S3 → Create bucket

- Bucket name: yash-portfolio-site

- Region: Choose nearest (us-east-1)

- Uncheck Block all public access

- Acknowledge the warning.

2. Enable Static Website Hosting

- Go to Properties → Static website hosting

- Select Enable

- Index document: index.html

- Save changes.

3. Upload your build files

- Upload everything inside the dist/ folder.

4. Go to Permissions → Bucket Policy and add:

```{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::yash-portfolio-site/*"
    }
  ]
}
```  

<img width="2558" height="547" alt="image" src="https://github.com/user-attachments/assets/0949c416-3030-44eb-89ad-d242c405acc3" />


3️⃣ Set Up CloudFront Distribution

1. Go to CloudFront → Create distribution

2. Origin domain: Choose your S3 bucket.

3. Viewer protocol policy: Redirect HTTP to HTTPS.

4. Default root object: index.html

5. Save and deploy — wait for it to complete.

<img width="2520" height="901" alt="image" src="https://github.com/user-attachments/assets/f671932e-eb59-4e6c-9c80-42240b4c6b4f" />


4️⃣ Test Your Site

Visit the CloudFront URL, e.g.
👉 https://d3gfth7z464oze.cloudfront.net

You should see your Vue 3 portfolio live!

<img width="2523" height="1367" alt="image" src="https://github.com/user-attachments/assets/887ecdf7-c546-4550-8aed-af045e42791f" />
