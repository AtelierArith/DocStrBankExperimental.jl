```
assume_role(principal::AbstractAWSConfig, role; kwargs...) -> AbstractAWSConfig
```

Assumes the IAM `role` via temporary credentials via the `principal` entity. The `principal` entity must be included in the trust policy of the `role`.

[Role chaining](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-role-chaining) must be manually specified by multiple `assume_role` calls (e.g. "role-a" has permissions to assume "role-b": `assume_role(assume_role(AWSConfig(), "role-a"), "role-b")`).

# Arguments

  * `principal::AbstractAWSConfig`: The AWS configuration and credentials of the principal entity (user or role) performing the `sts:AssumeRole` action.
  * `role::AbstractString`: The AWS IAM role to assume. Either a full role ARN or just the role name. If only the role name is specified the role will be assumed to reside in the same account used in the `principal` argument.

# Keywords

  * `duration::Integer` (optional): Role session duration in seconds.
  * `mfa_serial::AbstractString` (optional): The identification number of the MFA device that is associated with the user making the `AssumeRole` API call. Either a serial number for a hardware device ("GAHT12345678") or an ARN for a virtual device ("arn:aws:iam::123456789012:mfa/user"). When specified a MFA token must be provided via `token` or an interactive prompt.
  * `token::AbstractString` (optional): The value provided by the MFA device. Only can be specified when `mfa_serial` is set.
  * `session_name::AbstractString` (optional): The unique role session name associated with this API request.
