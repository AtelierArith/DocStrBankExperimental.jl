```
users(uuid::UUID; registries::Array{RegistryInstance}=reachable_registries())
users(pkg_name::String, pkg_registry_name::String=GENERAL_REGISTRY; kwargs...)
users(pkg_name::String, pkg_registry::RegistryInstance; kwargs...))
```

Find the users of a given package.

# Arguments

  * `uuid::UUID`: UUID of the package.
  * `pkg_name::String`: Find users of this package.
  * `pkg_registry_name::String="General"`: Name of registry where `pkg_name` is registered. This is used to look up the UUID of `pkg_name`.

# Keywords

  * `registries::Array{RegistryInstance}=reachable_registries()`: Registries to search for users.

# Returns

  * `Array{String}`: All packages which are dependent on the given package.
