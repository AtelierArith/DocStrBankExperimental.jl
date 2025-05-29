```
gmsh_do_physicalnames(raw_PhysicalNames) -> NamedTuple
```

Split `raw_PhysicalNames` created by [`load_gmsh_file`](@ref) in to one `Dict` for each dimension.

# Arguments

  * `raw_PhysicalNames`: data about physical names in gmsh file,

# Keywords

# Returns

  * `NamedTuple`: one `Dict{Int,String}` for each dimension, `physicalTag => Name`:

      * physicalTag1DtoName,
      * physicalTag2DtoName,
      * physicalTag3DtoName.

# Throws
