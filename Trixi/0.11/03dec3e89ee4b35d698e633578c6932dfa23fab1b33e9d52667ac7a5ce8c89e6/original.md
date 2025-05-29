```
DissipationMatrixWintersEtal()
```

Creates the Roe-like entropy-stable matrix dissipation operator from Winters et al. (2017). This operator must be used together with an entropy-conservative two-point flux function  (e.g., [`flux_ranocha`](@ref) or [`flux_chandrashekar`](@ref)) to yield  an entropy-stable surface flux. The surface flux function can be initialized as:

```julia
flux_es = FluxPlusDissipation(flux_ec, DissipationMatrixWintersEtal())
```

The 1D and 2D implementations are adapted from the [Atum.jl library](https://github.com/mwarusz/Atum.jl/blob/c7ed44f2b7972ac726ef345da7b98b0bda60e2a3/src/balancelaws/euler.jl#L198). The 3D implementation is adapted from the [FLUXO library](https://github.com/project-fluxo/fluxo)

For the derivation of the matrix dissipation operator, see:

  * A. R. Winters, D. Derigs, G. Gassner, S. Walch, A uniquely defined entropy stable matrix dissipation operator  for high Mach number ideal MHD and compressible Euler simulations (2017). Journal of Computational Physics. [DOI: 10.1016/j.jcp.2016.12.006](https://doi.org/10.1016/j.jcp.2016.12.006).
