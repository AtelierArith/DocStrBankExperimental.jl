```julia
struct NormConservingPsP{T} <: PseudoPotentialIO.NumericPsP{T}
```

Type representing a numeric norm-conserving pseudopotential.

  * `checksum::Vector{UInt8}`: SHA1 Checksum
  * `Zatom::Any`: Total charge.
  * `Zval::Any`: Valence charge.
  * `lmax::Int64`: Maximum angular momentum.
  * `r::Union{Vector{T}, StepRangeLen{T}} where T`: Radial mesh.
  * `dr::Union{Vector{T}, T} where T`: Radial mesh spacing.
  * `Vloc::Vector`: Local part of the potential on the radial mesh (without an r² prefactor).
  * `β::OffsetArrays.OffsetArray{Array{Vector{T}, 1}, 1, Array{Array{Vector{T}, 1}, 1}} where T`: Nonlocal projectors β[l][n] on the radial mesh (with an r² prefactor).
  * `D::OffsetArrays.OffsetArray{Matrix{T}, 1, Array{Matrix{T}, 1}} where T`: Projector coupling coefficients D[l][n,m].
  * `χ::Union{Nothing, OffsetArrays.OffsetArray{Array{Vector{T}, 1}, 1, Array{Array{Vector{T}, 1}, 1}}} where T`: Pseudo-atomic wavefunctions χ[l][n] on the radial mesh (with an r² prefactor).
  * `ρcore::Union{Nothing, Vector{T}} where T`: Model core charge density on the radial mesh (with an r² prefactor).
  * `ρval::Union{Nothing, Vector{T}} where T`: Valence charge density on the radial mesh (with an r² prefactor).
