```
flux_winters_etal(u_ll, u_rr, orientation_or_normal_direction,
                  equations::PolytropicEulerEquations2D)
```

Entropy conserving two-point flux for isothermal or polytropic gases. Requires a special weighted Stolarsky mean for the evaluation of the density denoted here as `stolarsky_mean`. Note, for isothermal gases where `gamma = 1` this `stolarsky_mean` becomes the [`ln_mean`](@ref).

For details see Section 3.2 of the following reference

  * Andrew R. Winters, Christof Czernik, Moritz B. Schily & Gregor J. Gassner (2020) Entropy stable numerical approximations for the isothermal and polytropic Euler equations [DOI: 10.1007/s10543-019-00789-w](https://doi.org/10.1007/s10543-019-00789-w)
