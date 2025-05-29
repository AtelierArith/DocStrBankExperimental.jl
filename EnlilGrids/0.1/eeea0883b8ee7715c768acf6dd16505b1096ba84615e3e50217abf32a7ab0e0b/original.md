```
gmsh_do_entities(raw_Entities) -> NamedTuple
```

Split `raw_Entities` created by [`load_gmsh_file`](@ref) in to one `Dict` for each type of entity. Operates with only one physicalTag per entity.

# Arguments

  * `raw_Entities`: data about entities in gmsh file,

# Keywords

# Returns

  * `NamedTuple`: one `Dict{Int,String}` for each dimension, `entityTag => physicalTag`:

      * pointTagtoPhysicalTag,
      * curveTagtoPhysicalTag,
      * surfaceTagtoPhysicalTag,
      * volumeTagtoPhysicalTag.

# Throws
