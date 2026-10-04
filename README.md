\# AWS DevOps CI/CD Demo



\## 1. Project Title



AWS DevOps CI/CD Pipeline with Terraform, GitHub Actions, Amazon S3, IAM OIDC, Release Snapshots and Rollback



\## 2. Project Overview



This project demonstrates a complete AWS DevOps CI/CD pipeline using Terraform, GitHub Actions, Amazon S3, AWS IAM and GitHub OpenID Connect (OIDC).



The application is a simple static web application built using HTML, CSS and JavaScript.



Whenever code is pushed to the main branch, GitHub Actions automatically validates the application, authenticates with AWS using OIDC, creates a release snapshot, deploys the application to Amazon S3, verifies the deployment and performs a health check.



A separate manual rollback workflow is also implemented. It allows a previous application release to be restored using its Git commit SHA.



\## 3. Project Objective



The main objective of this project is to design and implement a working AWS DevOps CI/CD pipeline that demonstrates practical knowledge of cloud infrastructure, automation, deployment, security, monitoring and rollback.



The project demonstrates the following DevOps capabilities:



\- Infrastructure as Code using Terraform

\- AWS infrastructure provisioning

\- CI/CD automation using GitHub Actions

\- Automated application deployment

\- Static website hosting using Amazon S3

\- Secure GitHub-to-AWS authentication using OIDC

\- IAM role-based access control

\- Avoiding hardcoded AWS credentials

\- Release versioning using Git commit SHA

\- Automated deployment verification

\- Manual rollback to a previous release

\- Application health checking

\- Git and GitHub source-code management

\- DevOps troubleshooting

\- Project documentation



The overall objective is to create a repeatable deployment process:



Developer

&#x20;   |

&#x20;   | git push

&#x20;   v

GitHub Repository

&#x20;   |

&#x20;   v

GitHub Actions

&#x20;   |

&#x20;   | OIDC Authentication

&#x20;   v

AWS IAM

&#x20;   |

&#x20;   v

Amazon S3

&#x20;   |

&#x20;   v

Live Web Application



The rollback process is:



Previous Release

&#x20;   |

&#x20;   v

S3 Release Snapshot

&#x20;   |

&#x20;   v

Rollback Workflow

&#x20;   |

&#x20;   v

S3 Website

&#x20;   |

&#x20;   v

Health Check



\## 4. Assignment Implementation



This project implements the CI/CD Pipeline on AWS requirement.



The solution includes:



\- Infrastructure as Code

\- Automated CI/CD

\- AWS deployment

\- Secure AWS authentication

\- Release snapshots

\- Rollback capability

\- Deployment verification

\- Health checking

\- Documentation



\## 5. Architecture



The architecture consists of GitHub as the source-code repository, GitHub Actions as the CI/CD platform, AWS IAM OIDC as the authentication mechanism, Amazon S3 as the deployment and hosting platform, and Terraform as the Infrastructure as Code tool.



\### Main Architecture



&#x20;                        Developer

&#x20;                            |

&#x20;                            | git push

&#x20;                            v

&#x20;                   +------------------+

&#x20;                   | GitHub Repository|

&#x20;                   +--------+---------+

&#x20;                            |

&#x20;                            | Push to main

&#x20;                            v

&#x20;                   +------------------+

&#x20;                   |  GitHub Actions  |

&#x20;                   |      CI/CD       |

&#x20;                   +--------+---------+

&#x20;                            |

&#x20;                            | OIDC

&#x20;                            v

&#x20;                   +------------------+

&#x20;                   |     AWS IAM      |

&#x20;                   | GitHub OIDC Role |

&#x20;                   +--------+---------+

&#x20;                            |

&#x20;                            v

&#x20;                   +------------------+

&#x20;                   |    Amazon S3     |

&#x20;                   | Static Website   |

&#x20;                   +--------+---------+

&#x20;                            |

&#x20;                 +----------+----------+

&#x20;                 |                     |

&#x20;                 v                     v

&#x20;          Live Application      Release Snapshots

&#x20;          index.html            \_releases/

&#x20;          style.css             <commit-sha>/

&#x20;          script.js



\## 6. Rollback Architecture



&#x20;                GitHub Actions

&#x20;                      |

&#x20;                      |

&#x20;               Manual Workflow

&#x20;                      |

&#x20;                      v

&#x20;                Release SHA

&#x20;                      |

&#x20;                      v

&#x20;             S3 Release Snapshot

&#x20;                      |

&#x20;                      v

&#x20;               Download Release

&#x20;                      |

&#x20;                      v

&#x20;             Temporary Directory

&#x20;                      |

&#x20;                      v

&#x20;             Remove Current Files

&#x20;                      |

&#x20;                      v

&#x20;             Restore Selected Release

&#x20;                      |

&#x20;                      v

&#x20;                Verify Files

&#x20;                      |

&#x20;                      v

&#x20;                Health Check



\## 7. Technology Stack



| Technology | Purpose |

|------------|---------|

| AWS | Cloud platform |

| Amazon S3 | Static website hosting and deployment |

| AWS IAM | Access control |

| GitHub OIDC | Secure GitHub-to-AWS authentication |

| GitHub Actions | CI/CD automation |

| GitHub | Source-code repository |

| Terraform | Infrastructure as Code |

| AWS CLI | AWS resource management and verification |

| Git | Version control |

| HTML | Application structure |

| CSS | Application styling |

| JavaScript | Application functionality |

| PowerShell | Local Windows administration |



\## 8. AWS Region



The project uses the AWS Mumbai region.



AWS Region:



ap-south-1



\## 9. Amazon S3



Amazon S3 is used for:



\- Static website hosting

\- Application deployment

\- Release snapshot storage

\- Rollback source files



S3 bucket:



aws-cicd-demo-bcc33d56677b9a2cb6bdb0ba40



Website endpoint:



http://aws-cicd-demo-bcc33d56677b9a2cb6bdb0ba40.s3-website.ap-south-1.amazonaws.com/



\## 10. Application



The application is a simple static website.



Application directory:



app/

├── index.html

├── style.css

└── script.js



The application displays:



AWS DevOps CI/CD Demo



and:



Application deployed successfully through CI/CD.



The application is intentionally simple because the main purpose of this project is to demonstrate the DevOps CI/CD pipeline.



\## 11. Infrastructure as Code



Terraform is used to provision and manage the AWS infrastructure.



Terraform files are stored inside:



iac/



The directory contains:



iac/

├── provider.tf

├── variables.tf

├── s3.tf

├── iam.tf

├── outputs.tf

└── .terraform.lock.hcl



\### provider.tf



Defines the Terraform providers and AWS region.



\### variables.tf



Defines configurable Terraform variables such as the AWS region.



\### s3.tf



Creates and configures:



\- S3 bucket

\- Static website configuration

\- Public access settings

\- S3 bucket policy



\### iam.tf



Creates and configures:



\- GitHub OIDC provider

\- IAM role

\- IAM trust policy

\- S3 deployment permissions



\### outputs.tf



Provides useful Terraform outputs such as:



\- S3 bucket name

\- Website endpoint

\- IAM role ARN



\## 12. Terraform Commands



Initialize Terraform:



terraform init



Validate Terraform configuration:



terraform validate



Create an execution plan:



terraform plan



Apply infrastructure:



terraform apply



Display Terraform state:



terraform show



The final Terraform plan verification returned:



No changes. Your infrastructure matches the configuration.



This confirms that the AWS infrastructure matches the Terraform configuration.



\## 13. AWS IAM and GitHub OIDC



GitHub Actions requires permission to access AWS.



Instead of storing permanent AWS access keys inside GitHub, this project uses GitHub OpenID Connect (OIDC).



GitHub Actions requests temporary AWS credentials through an IAM role.



IAM role:



github-actions-aws-cicd-demo



IAM Role ARN:



arn:aws:iam::203374879162:role/github-actions-aws-cicd-demo



The IAM trust relationship restricts which GitHub repository and branch can assume the role.



This improves security because long-term AWS access keys are not stored in the GitHub repository.



\## 14. GitHub Actions CI/CD



The deployment workflow is:



.github/workflows/deploy.yml



The workflow is triggered whenever code is pushed to the main branch.



\### Deployment Pipeline



Git Push

&#x20;  |

&#x20;  v

Checkout Source Code

&#x20;  |

&#x20;  v

Validate Application

&#x20;  |

&#x20;  v

Configure AWS Credentials

&#x20;  |

&#x20;  v

Save Release Snapshot

&#x20;  |

&#x20;  v

Deploy Application to S3

&#x20;  |

&#x20;  v

Verify S3 Deployment

&#x20;  |

&#x20;  v

Health Check

&#x20;  |

&#x20;  v

Deployment Completed



\## 15. Application Validation



Before deployment, GitHub Actions validates the required application files.



The workflow checks:



app/index.html

app/style.css

app/script.js



It also checks that the expected application title exists.



If validation fails, the deployment stops.



This prevents an invalid application from being deployed.



\## 16. Release Snapshots



Before deploying the current application, the pipeline saves a copy of the application using the Git commit SHA.



The release structure is:



\_releases/

├── <commit-sha-1>/

│   ├── index.html

│   ├── script.js

│   └── style.css

│

└── <commit-sha-2>/

&#x20;   ├── index.html

&#x20;   ├── script.js

&#x20;   └── style.css



Verified releases include:



7aba6d31e4921c083cfe730311b528bc5f445b1d



and:



a832edab281b238bb62d7ddec6986bd2d9cb1089



Each release contains:



index.html

script.js

style.css



\## 17. Why Release Snapshots Are Used



Release snapshots provide a simple rollback mechanism.



If a new deployment has a problem, a previous known-good release can be selected using its Git commit SHA.



Example:



Current Release

&#x20;     |

&#x20;     v

Problem Found

&#x20;     |

&#x20;     v

Select Previous SHA

&#x20;     |

&#x20;     v

Download Previous Snapshot

&#x20;     |

&#x20;     v

Restore to S3

&#x20;     |

&#x20;     v

Health Check



\## 18. Deployment to Amazon S3



The deployment workflow uses AWS CLI commands inside GitHub Actions.



The application files from:



app/



are synchronized to:



s3://aws-cicd-demo-bcc33d56677b9a2cb6bdb0ba40/



The deployment uses:



aws s3 sync



The --delete option removes old files from the website root that are no longer part of the current application.



The \_releases/ directory is excluded from deletion so previous release snapshots are preserved.



\## 19. Deployment Verification



After deployment, the workflow verifies that the application files exist in S3.



Expected files:



index.html

script.js

style.css



The workflow also performs an HTTP health check.



Health check command:



curl.exe -I http://aws-cicd-demo-bcc33d56677b9a2cb6bdb0ba40.s3-website.ap-south-1.amazonaws.com/



Successful result:



HTTP/1.1 200 OK



The final verification returned:



HTTP/1.1 200 OK

Content-Length: 698

Content-Type: text/html

Server: AmazonS3



This confirms that the deployed application is reachable.



\## 20. Rollback Workflow



The rollback workflow is:



.github/workflows/rollback.yml



The workflow uses workflow\_dispatch, which means rollback is manually triggered from GitHub Actions.



The user provides the Git commit SHA of the release that should be restored.



Example:



a832edab281b238bb62d7ddec6986bd2d9cb1089



\## 21. Rollback Process



The rollback workflow performs the following steps:



1\. Checkout source code.

2\. Configure AWS credentials using OIDC.

3\. Validate that the selected release exists.

4\. Download the selected release from S3.

5\. Verify index.html.

6\. Verify script.js.

7\. Verify style.css.

8\. Remove the current deployment.

9\. Restore the selected release.

10\. Verify the restored files.

11\. Perform a health check.

12\. Report rollback completion.



\## 22. Rollback Test



A rollback was successfully tested using:



a832edab281b238bb62d7ddec6986bd2d9cb1089



The rollback workflow completed successfully.



After rollback, the live website returned:



HTTP/1.1 200 OK



This proves that a previous release can be restored successfully.



\## 23. GitHub Repository



GitHub repository:



https://github.com/thara-user/aws-cicd-demo



\## 24. Project Structure



aws-cicd-demo/

│

├── .github/

│   └── workflows/

│       ├── deploy.yml

│       └── rollback.yml

│

├── app/

│   ├── index.html

│   ├── style.css

│   └── script.js

│

├── architecture/

│

├── iac/

│   ├── provider.tf

│   ├── variables.tf

│   ├── s3.tf

│   ├── iam.tf

│   ├── outputs.tf

│   └── .terraform.lock.hcl

│

├── pipeline/

│

├── .gitignore

│

└── README.md



\## 25. CI/CD Deployment Procedure



\### Step 1: Clone the Repository



git clone https://github.com/thara-user/aws-cicd-demo.git

cd aws-cicd-demo



\### Step 2: Initialize Terraform



cd iac

terraform init



\### Step 3: Validate Terraform



terraform validate



\### Step 4: Review Infrastructure



terraform plan



\### Step 5: Apply Infrastructure



terraform apply



\### Step 6: Return to Project Root



cd ..



\### Step 7: Make Application Changes



Modify the files inside:



app/



\### Step 8: Commit Changes



git add .

git commit -m "Update application"



\### Step 9: Push to GitHub



git push origin main



\### Step 10: GitHub Actions



The push automatically triggers the deployment workflow.



GitHub Actions performs:



Validation

&#x20;  |

&#x20;  v

AWS Authentication

&#x20;  |

&#x20;  v

Release Snapshot

&#x20;  |

&#x20;  v

S3 Deployment

&#x20;  |

&#x20;  v

Verification

&#x20;  |

&#x20;  v

Health Check



\## 26. Testing



\### Check S3 Bucket



aws s3 ls s3://aws-cicd-demo-bcc33d56677b9a2cb6bdb0ba40/



Expected:



\_releases/

index.html

script.js

style.css



\### Check Release Snapshots



aws s3 ls s3://aws-cicd-demo-bcc33d56677b9a2cb6bdb0ba40/\_releases/



Expected releases include:



7aba6d31e4921c083cfe730311b528bc5f445b1d/

a832edab281b238bb62d7ddec6986bd2d9cb1089/



\### Check Specific Release



aws s3 ls s3://aws-cicd-demo-bcc33d56677b9a2cb6bdb0ba40/\_releases/7aba6d31e4921c083cfe730311b528bc5f445b1d/



Expected:



index.html

script.js

style.css



\### Check Live Website



curl.exe -I http://aws-cicd-demo-bcc33d56677b9a2cb6bdb0ba40.s3-website.ap-south-1.amazonaws.com/



Expected:



HTTP/1.1 200 OK



\## 27. Security



The project follows basic DevOps security practices.



\### GitHub OIDC



GitHub Actions uses OIDC to authenticate with AWS instead of storing permanent AWS access keys.



\### IAM Role



The deployment process uses an IAM role with permissions required for S3 deployment.



\### No Hardcoded AWS Secrets



AWS access keys and secret keys are not stored in the source code.



\### Terraform State



Terraform state files are excluded from Git using .gitignore.



The .gitignore contains:



.terraform/

\*.tfstate

\*.tfstate.\*

.env



\## 28. Monitoring and Logging



The project provides basic monitoring and verification using:



\- GitHub Actions workflow logs

\- AWS CLI output

\- S3 object verification

\- Deployment verification

\- HTTP health checks



The health check confirms that the website is accessible after deployment.



Successful response:



HTTP/1.1 200 OK



GitHub Actions also provides logs for each CI/CD step, making it possible to identify deployment failures.



\## 29. Challenges Solved



\### Challenge 1: CI/CD Deployment



The deployment workflow was configured to automatically deploy the application after a push to the main branch.



\### Challenge 2: Secure AWS Authentication



AWS authentication was implemented using GitHub OIDC instead of storing permanent AWS access keys in GitHub.



\### Challenge 3: Release Preservation



The deployment workflow was configured to preserve the \_releases/ directory.



This allows previous application versions to remain available.



\### Challenge 4: Rollback



A separate rollback workflow was implemented to restore a selected release.



\### Challenge 5: Rollback File Restoration



The rollback workflow downloads the selected release to a temporary directory before restoring it to the S3 website root.



This ensures that the required application files are available before the rollback begins.



\### Challenge 6: Deployment Verification



The deployment workflow verifies the S3 files and performs a live HTTP health check.



\### Challenge 7: Infrastructure Verification



Terraform was executed with:



terraform plan



The result was:



No changes. Your infrastructure matches the configuration.



This confirms that there is no infrastructure drift.



\## 30. Git Commit History



Important commits include:



7aba6d3 Fix AWS deployment workflow

6ea3078 Fix rollback workflow syntax and restore process

19bc6f4 Fix rollback file restoration

8693418 Add automated rollback workflow

a832eda Preserve S3 release snapshots during deployment



\## 31. Final Validation



The project was successfully verified.



| Component | Status |

|-----------|--------|

| Terraform Infrastructure | Successful |

| Terraform Plan | No Changes |

| Amazon S3 | Successful |

| Static Website | Successful |

| GitHub Repository | Successful |

| GitHub Actions Deployment | Successful |

| AWS OIDC Authentication | Successful |

| Release Snapshots | Successful |

| Rollback Workflow | Successful |

| S3 File Verification | Successful |

| HTTP Health Check | HTTP 200 |

| Git Working Tree | Clean |



\## 32. Final CI/CD Flow



&#x20;                        Developer

&#x20;                            |

&#x20;                            | git push

&#x20;                            v

&#x20;                   GitHub Repository

&#x20;                            |

&#x20;                            v

&#x20;                   GitHub Actions

&#x20;                            |

&#x20;                            v

&#x20;                 Validate Application

&#x20;                            |

&#x20;                            v

&#x20;                 AWS OIDC Authentication

&#x20;                            |

&#x20;                            v

&#x20;                  Save Release Snapshot

&#x20;                            |

&#x20;                            v

&#x20;                   Deploy to Amazon S3

&#x20;                            |

&#x20;                            v

&#x20;                  Verify S3 Deployment

&#x20;                            |

&#x20;                            v

&#x20;                    HTTP Health Check

&#x20;                            |

&#x20;                            v

&#x20;                  Application Live



\## 33. Final Rollback Flow



&#x20;                Previous Release SHA

&#x20;                        |

&#x20;                        v

&#x20;               Rollback Workflow

&#x20;                        |

&#x20;                        v

&#x20;               Validate Snapshot

&#x20;                        |

&#x20;                        v

&#x20;               Download Release

&#x20;                        |

&#x20;                        v

&#x20;               Remove Current App

&#x20;                        |

&#x20;                        v

&#x20;               Restore Previous App

&#x20;                        |

&#x20;                        v

&#x20;                Verify Files

&#x20;                        |

&#x20;                        v

&#x20;                HTTP Health Check

&#x20;                        |

&#x20;                        v

&#x20;               Rollback Successful



\## 34. Final Result



The project successfully demonstrates an automated AWS DevOps CI/CD pipeline.



A developer can push code to the GitHub main branch, and GitHub Actions automatically validates and deploys the application to Amazon S3.



Each deployment creates a release snapshot identified by the Git commit SHA.



The project also provides a manual rollback mechanism that can restore a previous release.



The infrastructure is managed using Terraform, and GitHub Actions authenticates securely with AWS using OIDC.



The final live website was successfully verified with:



HTTP/1.1 200 OK



\## 35. Conclusion



This project demonstrates practical knowledge of:



\- AWS

\- Amazon S3

\- AWS IAM

\- GitHub Actions

\- GitHub OIDC

\- CI/CD

\- Terraform

\- Infrastructure as Code

\- Git

\- GitHub

\- AWS CLI

\- Deployment automation

\- Release management

\- Rollback strategies

\- Health checks

\- DevOps troubleshooting



The project provides a repeatable deployment process from source-code push to AWS deployment while maintaining release snapshots and rollback capability.



The implementation demonstrates how DevOps practices can be used to automate application delivery, improve deployment reliability and provide a controlled recovery mechanism when a deployment needs to be reverted.

