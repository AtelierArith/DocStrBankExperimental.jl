```
cocoBoot(cocoReg_fit, lags=[1:1:21;], n_bootstrap=400, alpha=0.05, n_burn_in=200, store_matrix = Array{Float64}(undef, length(lags), 2))
```

Bootstraps the partial autocorrelation function (PACF) for a fitted count regression model. It generates bootstrap samples of PACF values, computes quantiles to form confidence intervals, and then compares these intervals with the PACF computed from the observed data.

# Arguments

  * `cocoReg_fit`: A dictionary containing the fitted model results.
  * `lags` (optional): A vector of lag values for which the PACF is computed (default is `[1:1:21;]`).
  * `n_bootstrap` (optional): The number of bootstrap replications (default is 400).
  * `alpha` (optional): The significance level for the confidence intervals (default is 0.05).
  * `n_burn_in` (optional): The number of burn-in samples to discard when simulating data (default is 200).
  * `store_matrix` (optional): A preallocated matrix to store the lower and upper quantiles for each lag.

# Returns

A dictionary with the following keys:

  * `"upper"`: The lower quantile values (first column) of the bootstrapped PACF for each lag.
  * `"lower"`: The upper quantile values (second column) of the bootstrapped PACF for each lag.
  * `"in_interval"`: A Boolean vector indicating if the observed PACF values lie within the bootstrap confidence intervals.
  * `"pacf_data"`: The PACF computed from the observed data.
  * `"pacfs"`: The matrix of bootstrapped PACF values.
  * `"lags"`: The vector of lag values.
