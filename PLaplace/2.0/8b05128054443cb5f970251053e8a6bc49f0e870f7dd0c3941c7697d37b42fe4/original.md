```julia
xpnorm(
    p::Float64,
    v::AbstractVector{Float64},
    D::AbstractDict{Tuple{Int64, Int64}, SparseArrays.SparseMatrixCSC{Float64, Int64}},
    w::AbstractVector{Float64}
) -> Float64

```

Does the same as previous `xpnorm(...)`, but takes coefficient vector and derivate tensor as arguments instead of derivative vector.

Requires new mandatory arguments

  * `v::AbstractVector{Float64}`: Function discretely evaluated at the nodes of a mesh.
  * `D::AbstractDict{Tuple{Int64,Int64},SparseMatrixCSC{Float64,Int64}}`: Discrete derivative   tensor corresponding to the same nodes as v.

which replace

  * `dv::AbstractDict{Tuple{Int64,Int64},AbstractVector{Float64}}`
