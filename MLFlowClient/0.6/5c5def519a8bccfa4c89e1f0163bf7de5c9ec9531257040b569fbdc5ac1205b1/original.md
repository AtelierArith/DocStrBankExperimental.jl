```
setmodelversiontag(instance::MLFlow, name::String, key::String, value::String)
```

# Arguments

  * `instance:` [`MLFlow`](@ref) configuration.
  * `name:` Unique name of the model.
  * `version:` Model version number.
  * `key:` Name of the [`Tag`](@ref).
  * `value:` String value of the tag being logged.

# Returns

`true` if successful. Otherwise, raises exception.
