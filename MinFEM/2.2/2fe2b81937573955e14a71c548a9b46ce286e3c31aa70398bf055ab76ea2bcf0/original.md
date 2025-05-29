```julia
mutable struct Mesh
```

Type for a triangular finite element mesh with volume and boundary markers.

# Fields

  * `d::Int64`: Spatial dimension
  * `nnodes::Int64`: Number of nodes
  * `nelems::Int64`: Number of elements
  * `nboundelems::Int64`: Number of physical (marked) boundary elements
  * `Nodes::Vector{Vector{Float64}}`: List of node coordinates
  * `Elements::Vector{Vector{Int64}}`: List of element node indices
  * `BoundaryElements::Vector{Vector{Int64}}`: List of boundary element node indices
  * `ParentElements::Vector{Int64}`: List of parent elements to boundary elements
  * `ParentBoundaries::Vector{Int64}`: List of parent element local boundary to boundary elements
  * `Boundaries::Dict{Int64, MinFEM.Boundary}`: Dictionary of marked boundaries
  * `Domains::Dict{Int64, MinFEM.Domain}`: Dictionary of marked volume regions
  * `Entities::Vector{Dict{Int64, MinFEM.Entity}}`: Dictionary of physical entities
