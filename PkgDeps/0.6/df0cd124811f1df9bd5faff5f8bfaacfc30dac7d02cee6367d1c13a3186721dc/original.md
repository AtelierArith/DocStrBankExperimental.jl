```
dependencies(
    pkg_name::Union{AbstractString, Missing}, pkg_uuid::Union{Missing, UUID}=missing;
    registries::Array{RegistryInstance}=reachable_registries()
)
```

Find all packages that the latest version of `pkg_name` depends on (directly or indirectly).

Note: each package in the dependency tree is assumed to be at the latest version; compat bounds are ignored. Additionally, standard libraries are assumed to not have any dependencies.

# Arguments

  * `pkg_name::AbstractString`: Name of the package
  * `pkg_uuid::UUID`: UUID of the package, if available

# Keywords

  * `registries::Array{RegistryInstance}=reachable_registries()`: Registries to look into

# Returns

  * `Dict{String, UUID}()`: Packages which `pkg_name` depends on.
