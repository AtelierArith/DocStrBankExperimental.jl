```
compute_lipschitzconstant_boundary(
    gh::Array{Float64,1},
    coords::Array{Array{Float64,1},1},
    boundaryNodes::Set{Int64};
    qdim::Int64 = 1,
    pnorm::Real = 2
)
```

Returns Lipschitz constant of function g given as FEM coefficient vector on a boundary of the mesh.

# Mandatory Arguments

  * `gh::Array{Float64,1}`: Function discretely evaluated on a mesh.
  * `coords::Array{Array{Float64,1},1}`: Array of coordinates of the nodes gh was evaluated   on. In particular contains the coordinates of the boundaryNodes.
  * `boundaryNodes::Set{Int64}`: Set of nodes, i.e. entries in coords that belong to the   boundary that shall be evaluated. Therefore also selects entries of gh. Potentially   shifted by qdim.

# Keyword Arguments

  * `qdim::Int64 = 1`: Number of components of the function gh.
  * `pnorm::Real = 2`: Parameter of p-norm used to measure internal distances.
