```
min_max_speed_chen_noelle(u_ll, u_rr, orientation::Integer,
                          equations::ShallowWaterEquations2D)
min_max_speed_chen_noelle(u_ll, u_rr, normal_direction::AbstractVector,
                          equations::ShallowWaterEquations2D)
```

Special estimate of the minimal and maximal wave speed of the shallow water equations for the left and right states `u_ll, u_rr`. These approximate speeds are used for the HLL-type numerical flux [`flux_hll_chen_noelle`](@ref). These wave speed estimates together with a particular hydrostatic reconstruction technique guarantee that the numerical flux is positive and satisfies an entropy inequality.

Further details on this hydrostatic reconstruction and its motivation can be found in the reference below. The definition of the wave speeds are given in Equation (2.20).

  * Guoxian Chen and Sebastian Noelle (2017) A new hydrostatic reconstruction scheme based on subcell reconstructions [DOI:10.1137/15M1053074](https://dx.doi.org/10.1137/15M1053074)
