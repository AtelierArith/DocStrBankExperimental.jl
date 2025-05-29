```
gmsh_do_elements(raw_Elements) -> NamedTuple
```

Split `raw_Elements` created by [`load_gmsh_file`](@ref).

# Arguments

  * `raw_Elements`: data about elements in gmsh file,

# Keywords

# Returns

  * `NamedTuple`: one `Dict{Int,String}` for each dimension, `entityTag => physicalTag`:

      * entityTag1D   :: Array{Int64,1},
      * entityTag2D   :: Array{Int64,1},
      * entityTag3D   :: Array{Int64,1},
      * elementType1D :: Array{Int64,1},
      * elementType2D :: Array{Int64,1},
      * elementType3D :: Array{Int64,1},
      * elementTag1D  :: Array{Int64,1},
      * elementTag2D  :: Array{Int64,1},
      * elementTag3D  :: Array{Int64,1},
      * nodeTags1D    :: Array{Array{Int64,1},1},
      * nodeTags2D    :: Array{Array{Int64,1},1},
      * nodeTags3D    :: Array{Array{Int64,1},1}.

# Throws
