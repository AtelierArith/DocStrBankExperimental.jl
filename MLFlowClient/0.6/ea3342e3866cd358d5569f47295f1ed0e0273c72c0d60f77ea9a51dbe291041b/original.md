```
updateregisteredmodelpermission(instance::MLFlow, name::String, username::String,
    permission::Permission)
```

# Arguments

  * `instance:` [`MLFlow`](@ref) configuration.
  * `name:` [`RegisteredModel`](@ref) name.
  * `username:` [`User`](@ref) username.
  * `permission:` New [`Permission`](@ref) to grant.

# Returns

`true` if successful. Otherwise, raises exception.
