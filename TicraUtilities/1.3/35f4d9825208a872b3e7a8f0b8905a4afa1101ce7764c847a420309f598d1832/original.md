```
TEPperiodic <: TEP
```

Struct containing the data from a TICRA-compatible  Tabulated Electrical Properties (TEP) file for a periodic unit cell.  Note that  TEP files containing geometrical parameter sweeps are not yet supported.

## Fields

  * `name::String`: Object name of the periodic unit cell.
  * `class::String`: Class name of the periodic unit cell.
  * `theta`: An `AbstractRange` containing the θ values in units specified by field `atunit`.
  * `phi`: An `AbstractRange` containing the ϕ values in units specified by field `atunit`..
  * `freqs`: A vector of frequencies, each element of which is a `Unitful` quantity. The elements  may or may not all share the same frequency units.
  * `sff::Array{ComplexF64, 5}`: Contains reflection coefficients for front surface incidence.
  * `sfr::Array{ComplexF64, 5}`: Contains transmission coefficients for rear surface incidence.
  * `srf::Array{ComplexF64, 5}`: Contains transmission coefficients for front surface incidence.
  * `srr::Array{ComplexF64, 5}`: Contains reflection coefficients for rear surface incidence.

For `s` representing any of the fields `sff`, `sfr`, `srf`, and `srr`,  `size(s) = (2, 2, length(theta), length(phi), length(freqs))`, and the 2×2 matrix `s[:,:,i,j,k]`  is arranged in the order `[sTETE sTETM; sTMTE sTMTM]`.

## See Also

  * `TEPscatter`
