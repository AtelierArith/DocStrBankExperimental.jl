```julia
propagateBelief(
    dfg,
    destvar,
    factors;
    solveKey,
    dens,
    N,
    needFreshMeasurements,
    dbg,
    logger,
    asPartial
)

```

Calculate the proposals and products on `destvert` using `factors` in factor graph `dfg`.

Notes

  * Returns tuple of product and whether full dimensional (=true) or partial (=false).
  * `N` determines the number of samples to draw from the marginal.
  * `dens` can contain mixed full and partial dimension `ManifoldKernelDensity` beliefs

Related

[`approxConvBelief`](@ref), [`proposalbeliefs!`](@ref), [`AMP.manifoldProduct`](@ref)
