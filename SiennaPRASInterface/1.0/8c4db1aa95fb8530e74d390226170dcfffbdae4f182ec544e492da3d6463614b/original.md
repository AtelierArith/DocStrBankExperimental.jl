```
generate_pras_system(sys_location::String, aggregation; kwargs...)
```

Generate a PRAS SystemModel from a Sienna/Data PowerSystems System JSON file.

# Arguments

  * `sys_location::String`: Location of the Sienna/Data PowerSystems System JSON file
  * `aggregation::Type{AT}`: Aggregation topology type
  * `lump_region_renewable_gens::Bool`: Lumping of region renewable generators
  * `export_location::Union{Nothing, String}`: Export location of the .pras file

# Returns

  * `PRASCore.SystemModel`: PRAS SystemModel
