```
TEPscatter <: TEP
```

Struct containing the data for a single frequency from a TICRA-compatible  Tabulated Electrical Properties (TEP) file for a scattering surface (i.e., the old-style, original definition of TEP file in use since GRASP8.)

## Fields

  * `title::String`: Contains the title string.
  * `theta`: An `AbstractRange` containing the θ values in degrees.
  * `phi`: An `AbstractRange` containing the ϕ values in degrees.
  * `sff::Array{ComplexF64, 4}`: Contains reflection coefficients for front surface incidence.
  * `sfr::Array{ComplexF64, 4}`: Contains transmission coefficients for rear surface incidence.
  * `srf::Array{ComplexF64, 4}`: Contains transmission coefficients for front surface incidence.
  * `srr::Array{ComplexF64, 4}`: Contains reflection coefficients for rear surface incidence.

For `s` representing any of the fields `sff`, `sfr`, `srf`, and `srr`,  `size(s) = (2, 2, length(theta), length(phi))`, and the 2×2 matrix `s[:,:,i,j]`  is arranged in the order `[sθθ sθϕ; sϕθ sϕϕ]`.

## See Also

  * `TEPperiodic`
