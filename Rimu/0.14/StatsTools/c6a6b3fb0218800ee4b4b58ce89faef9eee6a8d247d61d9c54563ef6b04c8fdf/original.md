```
blocking_analysis(v::AbstractVector; α = 0.01, corrected = true, skip=0, warn=true)
-> BlockingResult(mean, err, err_err, p_cov, k, blocks)
```

Compute the sample mean `mean` and estimate the standard deviation of the mean (standard error) `err` of a correlated time series. It uses the blocking algorithm from Flyvberg and Peterson [JCP (1989)](http://aip.scitation.org/doi/10.1063/1.457480) and the M test of Jonsson [PRE (2018)](https://link.aps.org/doi/10.1103/PhysRevE.98.043304) at significance level $1-α$.

Use `skip` to skip the first `skip` elements in `v`. `corrected` controls whether bias correction for variances is used. If decorrelating the time series fails according to the M test, `NaN` is returned as the standard error and `-1` for `k`. The keyword argument `warn` controls whether a warning message is logged.

The summary result is returned as a [`BlockingResult`](@ref). `k - 1` is the number of blocking transformations required to pass the hypothesis test for an uncorrelated time series and `err_err` the estimated standard error or `err`.

The detailed results from each reblocking step can be obtained with [`blocking_analysis_data`](@ref).

See [`BlockingResult`](@ref), [`shift_estimator`](@ref), [`ratio_of_means`](@ref), [`blocking_analysis_data`](@ref).
