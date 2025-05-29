`BZ` is a data type representing a discretized Brillouin Zone in momentum space.

# Attributes

  * `basis           :: Vector{ Vector{ Float64 } }`: reciprocal lattice vectors of the Brillouin Zone.
  * `gridSize        :: Vector{Int64}`: The number of points along each dimension of the grid.
  * `kInds           :: Vector{Array{Float64}}`: the [`Monkhorst`](@ref) grid corresponding to k along bs.
  * `ks   	       :: Array{Vector{Float64}}`: The grid of momentum vectors k.
  * `HighSymPoints   :: Dict`: A dictionary containing the HIgh-Symmetry points Γ, K(2), and M(3).
  * `shift           :: Vector{Int64}` : how shifted the grid is from its centre point at the Γ point, in units of `1/gridSize`.

Initialize this structure using 

```julia
BZ(gridSize::Int64) --> defaults to dims = 2
BZ(gridSize::Int64, dims) --> Uniform grid in dimension = dims
BZ(gridSize::Vector{Int64})
```
