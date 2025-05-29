```
mean_and_cov(x, [wv::AbstractWeights,] vardim=1; corrected=false) -> (mean, cov)
```

Return the mean and covariance matrix as a tuple. A weighting vector `wv` can be specified. `vardim` that designates whether the variables are columns in the matrix (`1`) or rows (`2`). Finally, bias correction is applied to the covariance calculation if `corrected=true`. See [`cov`](@ref) documentation for more details.
