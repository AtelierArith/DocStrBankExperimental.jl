FermiSurface encodes information about one Fermi surface. It is usually constructed from Marching Tetrahedra method.

# Fields

  * `rlat::SMatrix{3,3,Float64,9}`, the reciprocal lattice vectors stored in columns
  * `ks::Matrix{Float64}`, a list of reduced k points on the Fermi surface.
  * `faces::Matrix{Int64}`, a set of triangles connecting neighbouring k points on the Fermi surface.
  * `weights::Vector{Float64}`, the area associated with each k point.
  * `bandidx::Union{Missing,Int64}`, the band index.

# Construction method

```julia
FermiSurface(rlat::AbstractMatrix{<:Real}, ks::AbstractMatrix{<:Real}, faces::AbstractMatrix{<:Integer})
```
