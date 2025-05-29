```
mahalanobisSquaredMatrix(data::DataFrame; meanvector=nothing, covmatrix=nothing)
```

Calculate Mahalanobis distances.

# Arguments

  * `data::DataFrame`: A DataFrame object of the multivariate data.
  * `meanvector::AbstractVector{Float64}`: Optional mean vector of variables.
  * `covmatrix::AbstractMatrix{Float64}`: Optional covariance matrix of data.

# References

Mahalanobis, Prasanta Chandra. "On the generalized distance in statistics."  National Institute of Science of India, 1936.
