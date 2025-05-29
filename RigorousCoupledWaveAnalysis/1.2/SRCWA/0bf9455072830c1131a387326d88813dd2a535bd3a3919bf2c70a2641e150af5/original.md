```
concatenate(S11a,S12a,S21a,S22a,S11b,S12b,S21b,S22b)
concatenate(S1::ScatterMatrix,S2::ScatterMatrix)
concatenate(Sin::Array{ScatterMatrix,1})
```

Computes the total scattering matrix for combined layers through concatenation

# Arguments

  * `S11a` : S11 component of the first scattering matrix
  * `S12a` : S12 component of the first scattering matrix
  * `S21a` : S21 component of the first scattering matrix
  * `S22a` : S22 component of the first scattering matrix
  * `S11b` : S11 component of the second scattering matrix
  * `S12b` : S12 component of the second scattering matrix
  * `S21b` : S21 component of the second scattering matrix
  * `S22b` : S22 component of the second scattering matrix
  * `S1` : first scattering matrix
  * `S2` : second scattering matrix
  * `Sin` : array of scattering matrices (chain concatenation)

# Outputs

  * `Sout` : total scattering matrix
