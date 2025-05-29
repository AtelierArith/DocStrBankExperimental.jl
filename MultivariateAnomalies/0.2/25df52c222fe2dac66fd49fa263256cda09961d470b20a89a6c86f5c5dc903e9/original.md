```
T2{tp}(data::AbstractArray{tp,2}, Q::AbstractArray[, mv])
```

Compute Hotelling's T2 control chart (the squared Mahalanobis distance to the data's mean vector (`mv`), given the covariance matrix `Q`). Input data is a two dimensional data matrix (observations * variables).

Lowry, C. A., & Woodall, W. H. (1992). A Multivariate Exponentially Weighted Moving Average Control Chart. Technometrics, 34, 46–53.
