```
@service module_name feature=val...
```

Include a high-level service wrapper based off of the `module_name` parameter optionally supplying a list of `features`.

When calling the macro you cannot match the predefined constant for the low-level API. The low-level API constants are named in all lowercase, and spaces replaced with underscores.

Examples:

```julia
using AWS.AWSServices: secrets_manager
using AWS: @service

# This matches the constant and will error!
@service secrets_manager
> ERROR: cannot assign a value to variable AWSServices.secrets_manager from module Main

# This does NOT match the filename structure and will error!
@service secretsmanager
> ERROR: could not open file /.julia/dev/AWS.jl/src/services/secretsmanager.jl

# All of the examples below are valid!
@service Secrets_Manager
@service SECRETS_MANAGER
@service sECRETS_MANAGER

# Using a feature
@service Secrets_Manager use_response_type = true
```

# Arguments

  * `module_name::Symbol`: Name of the module and service to include high-level API wrappers in your namespace
  * `features=val...`: A list of features to enable/disable for this high-level API include. See `FeatureSet` for a list of available features.

# Return

  * `Expression`: Module which embeds the high-level service API wrapper functions in your namespace
