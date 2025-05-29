```
    bacon(setting, m, method, alpha)
```

Run the BACON algorithm to detect outliers on regression data.

# Arguments:

  * `setting`: RegressionSetting object with a formula and a dataset.
  * `m`: The number of elements to be included in the initial subset.
  * `method`: The distance method to use for selecting the points for initial subset
  * `alpha`: The quantile used for cutoff

# Description

BACON (Blocked Adaptive Computationally efficient Outlier Nominators) algoritm, defined in the citation below, has many versions, e.g BACON for multivariate data, BACON for regression etc. Since the design matrix of a regression model is multivariate data, BACON for multivariate data is performed in early stages of the algorithm. After selecting a clean subset of observations, then a forward search is applied. Observations with high studendized residuals are reported as outliers.

# Output

  * `["outliers"]`: Array of indices of outliers.
  * `["betas"]`: Array of estimated coefficients.

# Examples

```julia-repl
julia> reg = createRegressionSetting(@formula(stackloss ~ airflow + watertemp + acidcond), stackloss)
julia> bacon(reg, m=12)
Dict{String, Vector} with 2 entries:
  "betas"    => [-37.6525, 0.797686, 0.57734, -0.0670602]
  "outliers" => [1, 3, 4, 21]
```

# References

Billor, Nedret, Ali S. Hadi, and Paul F. Velleman. "BACON: blocked adaptive computationally efficient outlier nominators." Computational statistics & data analysis 34.3 (2000): 279-298.
