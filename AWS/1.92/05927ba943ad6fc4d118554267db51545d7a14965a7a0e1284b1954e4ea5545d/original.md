```
AWSCredentials(; profile=nothing) -> Union{AWSCredentials, Nothing}
```

Create an AWSCredentials object, given a provided profile (if not provided "default" will be used).

Checks credential locations in the order:     1. Environment Variables     2. ~/.aws/credentials     3. ~/.aws/config     4. EC2 or ECS metadata

# Keywords

  * `profile::AbstractString`: Specific profile used to search for AWSCredentials

# Throws

  * `error("Can't find AWS Credentials")`: AWSCredentials could not be found
