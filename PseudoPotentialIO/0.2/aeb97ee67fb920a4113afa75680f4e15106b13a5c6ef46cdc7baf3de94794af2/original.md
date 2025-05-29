```julia
struct UltrasoftPsP{T} <: PseudoPotentialIO.NumericPsP{T}
```

Type representing a numeric ultrasoft pseudopotential.

  * `Zatom::Any`: Total charge
  * `Zval::Any`: Valence charge
  * `lmax::Int64`: Maximum angular momentum
  * `r::Vector`: Radial mesh
  * `dr::Union{Vector{T}, T} where T`: Radial mesh spacing
  * `Vloc::Vector`: Local part of the potential on the radial mesh
  * `β::OffsetArrays.OffsetArray{Array{Vector{T}, 1}, 1, Array{Array{Vector{T}, 1}, 1}} where T`: Nonlocal projectors β[l][n] on the radial mesh
  * `D::OffsetArrays.OffsetArray{Matrix{T}, 1, Array{Matrix{T}, 1}} where T`: Projector coupling coefficients D[l][n,m]
  * `χ::OffsetArrays.OffsetArray{Array{Vector{T}, 1}, 1, Array{Array{Vector{T}, 1}, 1}} where T`: Pseudo-atomic wavefunctions χ[l][n] on the radial mesh.
  * `Q::OffsetArrays.OffsetArray{Array{Vector{T}, 2}, 1, Array{Array{Vector{T}, 2}, 1}} where T`: Augmentation charge density functions Q[l][n,m] on the radial mesh
  * `q::OffsetArrays.OffsetArray{Matrix{T}, 1, Array{Matrix{T}, 1}} where T`: Augmentation charges q[l][n,m]
  * `ρcore::Union{Nothing, Vector{T}} where T`: Model core charge density for non-linear core correction on the radial mesh
  * `ρval::Union{Nothing, Vector{T}} where T`: Valence charge density for charge density initialization on the radial mesh
