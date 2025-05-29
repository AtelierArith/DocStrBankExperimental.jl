```
compute_random_pacfs(cocoReg_fit, lags, n_bootstrap=400, n_burn_in=200, pacfs=Array{Float64}(undef, n_bootstrap, length(lags)))
```

Generates bootstrapped partial autocorrelation coefficients by simulating new datasets from the fitted model. For each bootstrap iteration, it simulates data using `cocoSim` and computes the PACF for the specified lags.

# Arguments

  * `cocoReg_fit`: A dictionary containing the fitted model parameters and observed data.
  * `lags`: A vector of lag values at which to compute the PACF.
  * `n_bootstrap` (optional): The number of bootstrap samples (default is 400).
  * `n_burn_in` (optional): The number of burn-in samples to discard during simulation (default is 200).
  * `pacfs` (optional): A preallocated matrix to store the PACF values from each bootstrap sample.

# Returns

A matrix of bootstrapped PACF values with dimensions `(n_bootstrap, length(lags))`.
