```
setregisteredmodeltag(instance::MLFlow, name::String, key::String, value::String)
```

# Arguments

  * `instance:` [`MLFlow`](@ref) configuration.
  * `name:` Unique name of the model.
  * `key:` Name of the [`Tag`](@ref).
  * `value:` String value of the [`Tag`](@ref) being logged.

# Returns

`true` if successful. Otherwise, raises exception.
