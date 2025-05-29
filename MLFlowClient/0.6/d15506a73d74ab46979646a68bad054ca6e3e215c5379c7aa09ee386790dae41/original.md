```
deleteregisteredmodeltag(instance::MLFlow, name::String, key::String)
```

# Arguments

  * `instance:` [`MLFlow`](@ref) configuration.
  * `name:` Name of the [`RegisteredModel`](@ref) that the tag was logged under.
  * `key:` Name of the [`Tag`](@ref).

# Returns

`true` if successful. Otherwise, raises exception.
