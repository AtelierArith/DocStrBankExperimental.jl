```julia
struct HghPsP{T} <: PseudoPotentialIO.AnalyticalPsP
```

Analytical Hartwigsen-Goedecker-Hutter pseudopotential.

[C. Hartwigsen, S. Goedecker, and J. Hutter. *Pys. Rev. B* **58**, 3641 (1998)](https://doi.org/10.1103/PhysRevB.58.3641)

  * `checksum::Vector{UInt8}`: SHA1 Checksum
  * `Zatom::Union{Nothing, T} where T`: Atomic charge
  * `Zval::Any`: Valence charge
  * `lmax::Int64`: Maximum angular momentum
  * `rloc::Any`: Radial cutoff for the local part of the pseudopotential
  * `cloc::Vector`: Polynomial coefficience of the local part of the pseudopotential
  * `rnl::OffsetArrays.OffsetArray{T, 1, Vector{T}} where T`: Radial cutoffs for the nonlocal projectors `rnl[l]`
  * `D::OffsetArrays.OffsetArray{Matrix{T}, 1, Array{Matrix{T}, 1}} where T`: Nonlocal projector coupling coefficients `D[l][n,m]`
