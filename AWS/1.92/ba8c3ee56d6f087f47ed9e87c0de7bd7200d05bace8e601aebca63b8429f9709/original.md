```
check_credentials(
    aws_creds::AWSCredentials, force_refresh::Bool=false
) -> AWSCredentials
```

Checks current AWSCredentials, refreshing them if they are soon to expire. If `force_refresh` is `true` the credentials will be renewed immediately

# Arguments

  * `aws_creds::AWSCredentials`: AWSCredentials to be checked / refreshed

# Keywords

  * `force_refresh::Bool=false`: `true` to refresh the credentials

# Throws

  * `error("Can't find AWS credentials!")`: If no credentials can be found
