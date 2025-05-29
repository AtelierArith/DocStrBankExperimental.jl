```
assume_role(role_arn, [role_session_name]) -> AWSConfig
```

Generate a new `AWSConfig` by assuming a new role. In order to use the assumed role you need to use this config in the various AWS calls you perform.

# Arguments

  * `role_arn::AbstractString`: The ARN of the role to assume.
  * `role_session_name::AbstractString`: An optional string which is the unique identifier for   the session name.

# Keywords

  * `config::AWSConfig`: The AWS configuration to use when assuming the role.
