```
roughness_length_heat(z0m, kB_h)
```

# Arguments

  * `z0m` : Roughness length for momentum (m). Can be calculated          by [`roughness_parameters`](@ref).
  * `kB_h` : kB^(-1) parameter of heat transfer, Output of [`aerodynamic_conductance!`](@ref)

# Details

The roughness length for water and heat (z0h) is calculated from the  relationship (e.g. Verma 1989):

${k_B}_h = ln(z_{0m}/z_{0h})$ 

it follows:

$z_{0h} = z_{0m} / e^{k_{B_h}}$

# References

  * Verma, S., 1989: Aerodynamic resistances to transfers of heat, mass and momentum. In: Estimation of areal evapotranspiration, IAHS Pub, 177, 13-20.
  * Rigden, A., Li, D., Salvucci, G., 2018: Dependence of thermal roughness length on friction  velocity across land cover types: A synthesis analysis using AmeriFlux data. Agricultural  and Forest Meteorology 249, 512-519.
