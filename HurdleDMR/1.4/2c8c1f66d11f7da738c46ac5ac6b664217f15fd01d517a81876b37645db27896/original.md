```
fit(HDMR,covars,counts; <keyword arguments>)
hdmr(covars,counts; <keyword arguments>)
```

Fit a Hurdle Distributed Multinomial Regression (HDMR) of counts on covars.

HDMR fits independent hurdle lasso regressions to each column of counts to approximate a multinomial, picks a segement of each path, and returns a coefficient matrix (wrapped in HDMRCoefs) representing point estimates for the entire multinomial (includes the intercept if one was included).

# Example:

```julia
  m = fit(HDMR,covars,counts)
```

# Arguments

  * `covars` n-by-p matrix of covariates
  * `counts` n-by-d matrix of counts (usually sparse)

# Keywords

  * `inpos=1:p` indices of covars columns included in model for positive counts
  * `inzero=1:p` indices of covars columns included in model for zero counts
  * `intercept::Bool=false` include a intercepts in each hurdle regression
  * `parallel::Bool=true` parallelize the poisson fits
  * `local_cluster::Bool=true` use local_cluster mode that shares memory across   parallel workers that is appropriate on a single multicore machine, or   remote cluster mode that is more appropriate when distributing across machines   for which sharing memory is costly.
  * `verbose::Bool=true`
  * `showwarnings::Bool=false`
  * `select::SegSelect=MinAICc()` path segment selection criterion
  * `kwargs...` additional keyword arguments passed along to fit(Hurdle,...)
