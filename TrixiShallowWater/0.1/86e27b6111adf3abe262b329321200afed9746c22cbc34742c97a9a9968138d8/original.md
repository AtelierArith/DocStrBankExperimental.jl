```
flux_hll_chen_noelle = FluxHLL(min_max_speed_chen_noelle)
```

An instance of [`Trixi.FluxHLL`](@extref) specific to the shallow water equations that uses the wave speed estimates from [`min_max_speed_chen_noelle`](@ref). This HLL flux is guaranteed to have zero numerical mass flux out of a "dry" element, maintain positivity of the water height, and satisfy an entropy inequality.

For complete details see Section 2.4 of the following reference

  * Guoxian Chen and Sebastian Noelle (2017) A new hydrostatic reconstruction scheme based on subcell reconstructions [DOI: 10.1137/15M1053074](https://doi.org/10.1137/15M1053074)
