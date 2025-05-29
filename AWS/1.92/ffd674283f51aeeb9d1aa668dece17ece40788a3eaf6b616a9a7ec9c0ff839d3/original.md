```
ecs_instance_credentials() -> Union{AWSCredentials, Nothing}
```

Retrieve credentials from the ECS credential endpoint. If the ECS credential endpoint is unavailable then `nothing` will be returned.

More information can be found at:

  * https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-iam-roles.html
  * https://docs.aws.amazon.com/sdkref/latest/guide/feature-container-credentials.html

# Returns

  * `AWSCredentials`: AWSCredentials from `ECS` credentials URI, `nothing` if the Env Var is   not set (not running on an ECS container instance)

# Throws

  * `StatusError`: If the response status is >= 300
  * `ParsingError`: Invalid HTTP request target
