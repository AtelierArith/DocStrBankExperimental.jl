```
hadi1992(multivariateData)
```

Perform Hadi (1992) algorithm for a given multivariate data. 

# Arguments

  * `multivariateData::AbstractMatrix{Float64}`: Multivariate data.

# Description

Algorithm starts with an initial subset and enlarges the subset to  obtain robust covariance matrix and location estimates. 

# Output

  * `["outliers"]`: Array of indices of outliers
  * `["critical.chi.squared"]`: Threshold value for determining being an outlier
  * `["rth.robust.distance"]`: rth robust distance, where (r+1)th robust distance is the first one that exceeds the threshold.

# Examples

```julia-repl
julia> multidata = hcat(hbk.x1, hbk.x2, hbk.x3);

julia> hadi1992(multidata)
Dict{Any,Any} with 3 entries:
  "outliers"              => [2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
  "critical.chi.squared" => 7.81473
  "rth.robust.distance"   => 5.04541
```

# Reference Hadi, Ali S. "Identifying multiple outliers in multivariate data."  Journal of the Royal Statistical Society: Series B (Methodological) 54.3 (1992): 761-771.
