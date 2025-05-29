```
load_gmsh(filename::AbstractString) -> NamedTuple
```

Loads `filename` into separete `Dict`s according to the gmsh file format style in ASCII mode.

# Arguments

  * `filename::AbstractString`: name of the file to be loaded,

# Keywords

# Returns

  * `NamedTuple`: gmsh file is separated into the `Dict`s:

      * physicalTagtoName - see [`gmsh_do_physicalnames`](@ref),
      * tagToPhysicalTag - see [`gmsh_do_entities`](@ref),
      * nodes - see [`gmsh_do_nodes`](@ref),
      * elements - see [`gmsh_do_elements`](@ref).

# Throws
