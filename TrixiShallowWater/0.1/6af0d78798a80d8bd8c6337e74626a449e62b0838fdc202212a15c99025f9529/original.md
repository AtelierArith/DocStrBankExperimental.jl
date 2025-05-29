```
dissipation_roe(u_ll, u_rr, orientation_or_normal_direction,
                                equations::ShallowWaterExnerEquations1D)
```

Roe-type dissipation term for the [`ShallowWaterExnerEquations1D`](@ref) with an approximate Roe average for the sediment discharge `q_s`.
