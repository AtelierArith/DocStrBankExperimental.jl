```
direct_dependencies(pkg_name::String;
    registries::Array{RegistryInstance}=reachable_registries()) -> Dict{String, UUID}
direct_dependencies(pkg_uuid::UUID; registries::Array{RegistryInstance}=reachable_registries()) -> Dict{String, UUID}
```

Returns the direct dependencies of the latest version of a given package in the form of `Dict` with names as keys and UUIDs as values.

Standard libraries are assumed to not have any dependencies.
