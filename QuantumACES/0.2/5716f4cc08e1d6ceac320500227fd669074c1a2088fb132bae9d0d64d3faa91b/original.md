```
calc_covariance(d::Design, noise_est::NoiseEstimate; weight_time::Bool = false)
calc_covariance(d_rand::RandDesign, noise_est::NoiseEstimate; weight_time::Bool = false)
```

Returns the estimated covariance matrix for a noise estimate `noise_est` associated with the design `d` or randomised design `d_rand`, weighting the shot budget by the time factor if `weight_time` is `true`.
