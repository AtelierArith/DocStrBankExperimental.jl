```julia
struct UpfFile <: PseudoPotentialIO.PsPFile
```

Universal Pseudopotential Format file contents.

  * `checksum::Vector{UInt8}`: SHA1 Checksum
  * `version::String`: UPF format version
  * `info::Union{Nothing, String}`: Optional general information about the pseudopotential, often generation input
  * `header::PseudoPotentialIO.UpfHeader`: Various pseudopotential metadata
  * `mesh::PseudoPotentialIO.UpfMesh`: Radial mesh, mesh integration factors, and other mesh information
  * `nlcc::Union{Nothing, Vector{Float64}}`: Pseudized core charge on the radial grid, (ignored if `core_correction` is false)
  * `local_::Union{Nothing, Vector{Float64}}`: Local part of the pseudopotential on the radial grid (ignored if `is_coulomb`)
  * `nonlocal::PseudoPotentialIO.UpfNonlocal`: Nonlocal part of the pseudopotential
  * `pswfc::Union{Nothing, Vector{PseudoPotentialIO.UpfChi}}`: Pseudo-atomic valence wavefunctions
  * `full_wfc::Union{Nothing, PseudoPotentialIO.UpfFullWfc}`: All-electron wavefunctions
  * `rhoatom::Vector{Float64}`: Pseudo-atomic valence charge density on the radial grid
  * `spin_orb::Union{Nothing, PseudoPotentialIO.UpfSpinOrb}`: Spin-orbit coupling data, (ignored if `has_so` is false)
  * `paw::Union{Nothing, PseudoPotentialIO.UpfPaw}`: PAW data, (ignored if `is_paw` is false)
  * `gipaw::Union{Nothing, PseudoPotentialIO.UpfGipaw}`: GIPAW data
