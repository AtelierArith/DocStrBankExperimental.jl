```
correlate_draws(raw_draws, data, nonlinear, cov, parameters)
```

Given independent standard normal draws in `raw_draws` (Vector of matrices length K, size n*obs×I), and a full estimated covariance structure in `parameters` (with keys :σ2*var and :σcov*var1*var2), returns a new set of draws that exhibit the specified correlations across dimensions.
