```julia
struct HghFile <: PseudoPotentialIO.PsPFile
```

Hartwigsen-Goedecker-Hutter pseudopotential file contents.

  * `checksum::Vector{UInt8}`: SHA1 Checksum
  * `title::String`: Description
  * `zion::Vector{Int64}`: Pseudo-atomic (valence) charge
  * `rloc::Float64`: Cutoff radius for the local part of the pseudopotential
  * `nloc::Int64`: Number of coefficients defining the local part of the pseudopotential
  * `cloc::Vector{Float64}`: Coefficients of the local part of the pseudopotential
  * `lmax::Int64`: Maximum angular momentum
  * `rp::Vector{Float64}`: Non-local projector cutoff radius for each angular momentum
  * `h::Vector{Matrix{Float64}}`: Kleinman-Bylander energies
