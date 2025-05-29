```
ratio_of_means(num, denom; α=0.01, corrected=true, mc_samples=nothing, skip=0, warn=true)
-> r::RatioBlockingResult
```

Estimate the ratio of `mean(num)/mean(denom)` assuming that `num` and `denom` are possibly correlated time series, skipping the first `skip` elements. A blocking analysis with m-test is used to uncorrelate the time series, see [`blocking_analysis`](@ref). The remaining standard error and correlation of the means is propagated using [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl). The results are reported as a [`RatioBlockingResult`](@ref).

Robust estimates for the ratio are obtained from `pmedian(r)` and confidence intervals from `pquantile()`, e.g. `pquantile(r, [0.025, 0.975])` for the 95% confidence interval.

Estimates from linear uncertainty propagation are returned as `r.f` and `r.σ_f` using [`x_by_y_linear`](@ref). The standard error estimate `r.σ_f` should only be trusted when the coefficient of variation `std(denom)/mean(denom)` is small: `abs(r.δ_y) < 0.1`. Under this condition can the ratio be approximated as a normal distribution. See [wikipedia](https://en.wikipedia.org/wiki/Propagation_of_uncertainty) and [Díaz-Francés, Rubio (2013)](http://link.springer.com/10.1007/s00362-012-0429-2)

The keyword `mc_samples` controls the number of samples used for error propagation by [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl). Use `nothing` for the default and `Val(1000)` to set the number to 1000 samples in a type-consistent way.

The keyword `warn` controls whether warning messages are logged when blocking fails or noisy denominators are encountered.

Note: to compute statistics on the [`RatioBlockingResult`](@ref), use functions `pmedian`, `pquantile`, `pmiddle`, `piterate`, `pextrema`, `pminimum`, `pmaximum`, `pmean`, and `pcov`.
