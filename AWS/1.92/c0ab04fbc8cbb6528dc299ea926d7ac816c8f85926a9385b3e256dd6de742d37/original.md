```
sso_credentials(profile=nothing) -> Union{AWSCredentials, Nothing}
```

Retrieve credentials via AWS single sign-on (SSO) settings defined in the `profile` within the AWS configuration file. If no SSO settings are found for the `profile` `nothing` is returned.

# Arguments

  * `profile`: Specific profile used to get `AWSCredentials`, default is `nothing`
