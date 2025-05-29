```
smr98(setting)
```

Perform the Sebert, Monthomery and Rollier (1998) algorithm for the given regression setting.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.

# Description

The algorithm starts with an ordinary least squares  estimation for a given model and data. Residuals and fitted responses are calculated  using the estimated model. A hierarchical clustering analysis is applied using standardized residuals and standardized fitted responses. The tree structure of clusters are cut using a threshold, e.g Majona criterion, as suggested by the authors. It is expected that  the subtrees with relatively small number of observations are declared to be clusters of outliers.

# Output

  * `["outliers"]`: Array of indices of outliers.
  * `["betas"]`: Vector of regression coefficients.

# Examples

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> smr98(reg0001)
Dict{String, Vector} with 2 entries:
  "betas"    => [-55.4519, 1.15692]
  "outliers" => [15, 16, 17, 18, 19, 20, 21, 22, 23, 24]
```

# References

Sebert, David M., Douglas C. Montgomery, and Dwayne A. Rollier. "A clustering algorithm for  identifying multiple outliers in linear regression." Computational statistics & data analysis  27.4 (1998): 461-484.
