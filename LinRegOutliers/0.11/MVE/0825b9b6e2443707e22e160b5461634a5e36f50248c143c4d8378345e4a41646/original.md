```
mve(data; alpha = 0.01)
```

Performs the Minimum Volume Ellipsoid algorithm for a robust covariance matrix.

# Arguments

  * `data::DataFrame`: Multivariate data.
  * `alpha::Float64`: Probability for quantiles of Chi-Squared statistic.

# Description

`mve` searches for a robust location vector and a robust scale matrix, e.g covariance matrix. The method also reports a usable diagnostic measure, Mahalanobis distances, which are calculated using  the robust counterparts instead of mean vector and usual covariance matrix. Mahalanobis distances  are directly comparible with quantiles of a ChiSquare Distribution with `p` degrees of freedom.

# Output

  * `["goal"]`: Objective value
  * `["best.subset"]`: Indices of best h-subset of observations
  * `["robust.location"]`: Vector of robust location measures
  * `["robust.covariance"]`: Robust covariance matrix
  * `["squared.mahalanobis"]`: Array of Mahalanobis distances calculated using robust location and scale measures.
  * `["chisq.crit"]`: Chisquare quantile used in threshold
  * `["alpha"]`: Probability used in calculating the Chisquare quantile, e.g `chisq.crit`
  * `["outliers"]`: Array of indices of outliers.

# References

Van Aelst, Stefan, and Peter Rousseeuw. "Minimum volume ellipsoid." Wiley  Interdisciplinary Reviews: Computational Statistics 1.1 (2009): 71-82.
