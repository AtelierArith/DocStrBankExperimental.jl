```
satman2015(setting)
```

Perform Satman (2015) algorithm for the given regression setting.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.

# Description

The algorithm starts with sorting the design matrix using the Non-dominated sorting algorithm. An initial basic subset is then constructed using the ranks obtained in previous stage. After many  C-steps, observations with high standardized residuals are reported to be outliers.

# Output

  * `["outliers]`": Array of indices of outliers.
  * `[betas]`: Array of regression coefficients.
  * `[residuals]`: Array of residuals.
  * `[standardized_residuals]`: Array of standardized residuals.

# Examples

```julia-repl
julia> eg0001 = createRegressionSetting(@formula(y ~ x1 + x2 + x3), hbk);
julia> satman2015(reg0001)
Dict{Any,Any} with 1 entry:
  "outliers" => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 14, 47]

```

# References

Satman, Mehmet Hakan. "Fast online detection of outliers using least-trimmed squares  regression with non-dominated sorting based initial subsets."  International Journal of Advanced Statistics and Probability 3.1 (2015): 53.
