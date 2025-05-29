```
gmsh_do_nodes(raw_Nodes) -> NamedTuple
```

Split `raw_Nodes` created by [`load_gmsh_file`](@ref). Operates with only non parametric curves.

# Arguments

  * `raw_Nodes`: data about nodes in gmsh file,

# Keywords

# Returns

  * `NamedTuple`: one `Dict{Int,String}` for each dimension, `entityTag => physicalTag`:

      * nodeTag::Array{Int64,1},
      * vx::Array{Float64,1},
      * vy::Array{Float64,1},
      * vz::Array{Float64,1}.

# Throws
