```
setruntag(instance::MLFlow, run_id::String, key::String, value::String)
setruntag(instance::MLFlow, run::Run, key::String, value::String)
setruntag(instance::MLFlow, run::Run, tag::Tag)
```

Set a [`Tag`](@ref) on a [`Run`](@ref).

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `run_id`: ID of the [`Run`](@ref) under which to log the [`Tag`](@ref).
  * `key`: Name of the [`Tag`](@ref).
  * `value`: String value of the [`Tag`](@ref) being logged.

# Returns

`true` if successful. Otherwise, raises exception.
