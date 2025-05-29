```
satman2013(setting)
```

Perform Satman (2013) algorithm for the given regression setting.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.

# Description

The algorithm constructs a fast and robust covariance matrix to calculate robust mahalanobis distances. These distances are then used to construct weights for later use in a weighted least  squares estimation. In the last stage, C-steps are iterated on the basic subset found in previous stages. 

# Output

  * `["outliers"]`: Array of indices of outliers.
  * `["betas"]`: Array of estimated regression coefficients.
  * `["residuals"]`: Array of residuals.

# Examples

```julia-repl
julia> eg0001 = createRegressionSetting(@formula(y ~ x1 + x2 + x3), hbk);
julia> satman2013(reg0001)
Dict{Any,Any} with 1 entry:
  "outliers" => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 47]
  "betas" => ...
  "residuals" => ...
```

# References

Satman, Mehmet Hakan. "A new algorithm for detecting outliers in linear regression."  International Journal of statistics and Probability 2.3 (2013): 101.
