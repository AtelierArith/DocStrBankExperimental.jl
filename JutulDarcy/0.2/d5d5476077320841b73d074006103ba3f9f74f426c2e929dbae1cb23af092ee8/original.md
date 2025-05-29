```
BrooksCoreyRelativePermeabilities(
    sys_or_nph::Union{MultiPhaseSystem, Integer},
    exponents = 1.0,
    residuals = 0.0,
    endpoints = 1.0
)
```

Secondary variable that implements the family of Brooks-Corey relative permeability functions. This is a simple analytical expression for relative permeabilities that has a limited number of parameters:

$K(S) = K_{max} * ((S - S_r)/(1 - S_r^{tot}))^N$

## Fields

  * `exponents`: Exponents for each phase
  * `residuals`: Residual saturations for each phase
  * `endpoints`: Maximum relative permeability for each phase
  * `residual_total`: Total residual saturation over all phases
