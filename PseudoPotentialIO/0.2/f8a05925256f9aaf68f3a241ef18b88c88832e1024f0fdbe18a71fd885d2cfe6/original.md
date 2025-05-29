```julia
struct Psp8File <: PseudoPotentialIO.PsPFile
```

ABINIT PSeudoPotential format 8 file contents. Information on the file format specification and the meaning of the quantities within the file can be found on the ["psp8" page](https://docs.abinit.org/developers/psp8_info/) of the ABINIT documentation.

  * `checksum::Vector{UInt8}`: SHA1 Checksum
  * `header::PseudoPotentialIO.Psp8Header`: Various pseudopotential metadata
  * `rgrid::Vector{Float64}`: Uniform radial grid starting at `r = 0.0`
  * `v_local::Vector{Float64}`: Local part of the pseudopotential
  * `projectors::Vector{Vector{Vector{Float64}}}`: Radial part of the Kleinman-Bylander projectors for each angular momentum
  * `ekb::Vector{Vector{Float64}}`: Kleinman-Bylander energies for each angular momentum
  * `projectors_so::Union{Nothing, Vector{Vector{Vector{Float64}}}}`: Radial part of the spin-orbit Kleinman-Bylander projectors for each angular momentum
  * `ekb_so::Union{Nothing, Vector{Vector{Float64}}}`: Spin-orbit Kleinman-Bylander energies for each angular momentum
  * `rhoc::Union{Nothing, Vector{Float64}}`: Model core charge density
  * `d_rhoc_dr::Union{Nothing, Vector{Float64}}`: First derivative of the model core charge density
  * `d2_rhoc_dr2::Union{Nothing, Vector{Float64}}`: Second derivative of the model core charge density
  * `d3_rhoc_dr3::Union{Nothing, Vector{Float64}}`: Third derivative of the model core charge density
  * `d4_rhoc_dr4::Union{Nothing, Vector{Float64}}`: Fourth derivative of the model core charge density
