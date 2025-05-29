```
AWSCredentials
```

When you interact with AWS, you specify your [AWS Security Credentials](http://docs.aws.amazon.com/general/latest/gr/aws-security-credentials.html) to verify who you are and whether you have permission to access the resources that you are requesting. AWS uses the security credentials to authenticate and authorize your requests. The fields `access_key_id` and `secret_key` hold the access keys used to authenticate API requests (see [Creating, Modifying, and Viewing Access Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html#Using_CreateAccessKey)). [Temporary Security Credentials](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp.html) require the extra session `token` field. The `user_arn` and `account_number` fields are used to cache the result of the [`aws_user_arn`](@ref) and [`aws_account_number`](@ref) functions.

AWS.jl searches for credentials in multiple locations and stops once any credentials are found. The credential preference order mostly [mirrors the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-authentication.html#cli-chap-authentication-precedence) and is as follows:

1. Credentials or a profile passed directly to the `AWSCredentials`
2. [Environment variables](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html)
3. [Web Identity](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-role.html#cli-configure-role-oidc)
4. [AWS Single Sign-On (SSO)](http://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sso.html) provided via the AWS configuration file
5. [AWS credentials file](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html) (e.g. "~/.aws/credentials")
6. [External process](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sourcing-external.html) set via `credential_process` in the AWS configuration file
7. [AWS configuration file](http://docs.aws.amazon.com/cli/latest/userguide/cli-config-files.html) set via `aws_access_key_id` in the AWS configuration file
8. [Amazon ECS container credentials](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-iam-roles.html)
9. [Amazon EC2 instance metadata](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html)

Once the credentials are found, the method by which they were accessed is stored in the `renew` field and the `DateTime` at which they will expire is stored in the `expiry` field. This allows the credentials to be refreshed as needed using [`check_credentials`](@ref). If `renew` is set to `nothing`, no attempt will be made to refresh the credentials. Any renewal function is expected to return `nothing` on failure or a populated `AWSCredentials` object on success. The `renew` field of the returned `AWSCredentials` will be discarded and does not need to be set.

To specify the profile to use from `~/.aws/credentials`, do, for example, `AWSCredentials(profile="profile-name")`.
