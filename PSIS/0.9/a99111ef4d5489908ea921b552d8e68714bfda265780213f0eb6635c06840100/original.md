```
PSISResult
```

Result of Pareto-smoothed importance sampling (PSIS) using [`psis`](@ref).

# Properties

  * `log_weights`: un-normalized Pareto-smoothed log weights
  * `weights`: normalized Pareto-smoothed weights (allocates a copy)
  * `pareto_shape`: Pareto $k=ξ$ shape parameter
  * `nparams`: number of parameters in `log_weights`
  * `ndraws`: number of draws in `log_weights`
  * `nchains`: number of chains in `log_weights`
  * `reff`: the ratio of the effective sample size of the unsmoothed importance ratios and the actual sample size.
  * `ess`: estimated effective sample size of estimate of mean using smoothed importance samples (see [`ess_is`](@ref))
  * `tail_length`: length of the upper tail of `log_weights` that was smoothed
  * `tail_dist`: the generalized Pareto distribution that was fit to the tail of `log_weights`. Note that the tail weights are scaled to have a maximum of 1, so `tail_dist * exp(maximum(log_ratios))` is the corresponding fit directly to the tail of `log_ratios`.
  * `normalized::Bool`:indicates whether `log_weights` are log-normalized along the sample dimensions.

# Diagnostic

The `pareto_shape` parameter $k=ξ$ of the generalized Pareto distribution `tail_dist` can be used to diagnose reliability and convergence of estimates using the importance weights [VehtariSimpson2021](@citep).

  * if $k < \frac{1}{3}$, importance sampling is stable, and importance sampling (IS) and PSIS both are reliable.
  * if $k ≤ \frac{1}{2}$, then the importance ratio distributon has finite variance, and the central limit theorem holds. As $k$ approaches the upper bound, IS becomes less reliable, while PSIS still works well but with a higher RMSE.
  * if $\frac{1}{2} < k ≤ 0.7$, then the variance is infinite, and IS can behave quite poorly. However, PSIS works well in this regime.
  * if $0.7 < k ≤ 1$, then it quickly becomes impractical to collect enough importance weights to reliably compute estimates, and importance sampling is not recommended.
  * if $k > 1$, then neither the variance nor the mean of the raw importance ratios exists. The convergence rate is close to zero, and bias can be large with practical sample sizes.

See [`PSISPlots.paretoshapeplot`](@ref) for a diagnostic plot.

# References

  * [VehtariSimpson2021](@cite) Vehtari et al. JMLR 25:72 (2021).
