```
flux_nonconservative_ersing_etal(u_ll, u_rr, orientation, equations::ShallowWaterExnerEquations1D)
```

Non-symmetric path-conservative two-point flux discretizing the nonconservative terms of the [`ShallowWaterExnerEquations1D`](@ref) which consists of the hydrostatic pressure of the fluid layer and an additional pressure contribution from the sediment layer to obtain an entropy inequality.

This non-conservative flux should be used together with [`flux_ersing_etal`](@ref) to create a scheme that is entropy conservative and well-balanced.
