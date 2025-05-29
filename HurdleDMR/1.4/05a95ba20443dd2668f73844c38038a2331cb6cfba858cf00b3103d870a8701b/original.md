```
fit(DMR,covars,counts; <keyword arguments>)
dmr(covars,counts; <keyword arguments>)
```

Fit a Distributed Multinomial Regression (DMR) of counts on covars.

DMR fits independent poisson gamma lasso regressions to each column of counts to approximate a multinomial, picks a segement of each path, and returns a coefficient matrix (wrapped in DMRCoefs) representing point estimates for the entire multinomial (includes the intercept if one was included).

# Example:

```julia
  m = fit(DMR,covars,counts)
```

# Arguments

  * `covars` n-by-p matrix of covariates
  * `counts` n-by-d matrix of counts (usually sparse)

# Keywords

  * `intercept::Bool=false` include an intercept in each poisson
  * `parallel::Bool=true` parallelize the poisson fits
  * `local_cluster::Bool=true` use local_cluster mode that shares memory across   parallel workers that is appropriate on a single multicore machine, or   remote cluster mode that is more appropriate when distributing across machines   for which sharing memory is costly.
  * `verbose::Bool=true`
  * `showwarnings::Bool=false`
  * `select::SegSelect=MinAICc()` which path segment to pick
  * `kwargs...` additional keyword arguments passed along to fit(GammaLassoPath,...)
