```julia
struct EnsembleSummary{T, N, Tt, S, S2, S3, S4, S5} <: SciMLBase.AbstractEnsembleSolution{T, N, S}
```

The `EnsembleSummary` type is included to help with analyzing the general summary statistics. Two constructors are provided:

```julia
EnsembleSummary(sim; quantiles = [0.05, 0.95])
EnsembleSummary(sim, ts; quantiles = [0.05, 0.95])
```

The first produces a `(mean,var)` summary at each time step. As with the summary statistics, this assumes that the time steps are all the same. The second produces a `(mean,var)` summary at each time point `t` in `ts`. This requires the ability to interpolate the solution. Quantile is used to determine the `qlow` and `qhigh` quantiles at each timepoint. It defaults to the 5% and 95% quantiles.

## Plot Recipe

The `EnsembleSummary` comes with a plot recipe for visualizing the summary statistics. The extra keyword arguments are:

  * `idxs`: the solution components to plot. Defaults to plotting all components.
  * `error_style`: The style for plotting the error. Defaults to `ribbon`. Other choices are `:bars` for error bars and `:none` for no error bars.
  * `ci_type` : Defaults to `:quantile` which has `(qlow,qhigh)` quantiles whose limits were determined when constructing the `EnsembleSummary`. Gaussian CI `1.96*(standard error of the mean)` can be set using `ci_type=:SEM`.

One useful argument is `fillalpha` which controls the transparency of the ribbon around the mean.
