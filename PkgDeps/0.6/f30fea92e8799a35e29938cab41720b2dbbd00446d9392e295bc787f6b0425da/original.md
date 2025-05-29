```
reachable_registries(registry_names::Array)
reachable_registries(registry_name::String; depots::Union{String, Vector{String}}=Base.DEPOT_PATH)
reachable_registries(; depots::Union{String, Vector{String}}=Base.DEPOT_PATH)
```

Get an array of found registries.

# Arguments

  * `registry_names::Array`: List of registries to retrieve

# Keywords

  * `depots::Union{String, Vector{String}}=Base.DEPOT_PATH`: Depots to look in for registries

# Returns

  * `Array{RegistryInstance}`: List of all found registries
