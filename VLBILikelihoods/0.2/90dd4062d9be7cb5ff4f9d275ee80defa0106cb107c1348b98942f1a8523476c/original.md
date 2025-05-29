```
ComplexVisLikelihood(μ::AbstractVector{<:StaticMatrix{2,2}}, Σ::AbstractVector{<:StaticMatrix{2,2, <:Real}})
```

Creates the coherency matrix likelihood distribution which is a Gaussian over the space of 2×2 complex visibilities.

## Paramters

  * `μ`: The mean coherency matrix stored as a vector of 2x2 static matrices, which is usually computed from some VLBI model
  * `Σ`: The measurement covariance matrix, which is usually computed directly from the data.      Note that `Σ` must vector of 2x2 real static matrices.

!!! notes
    You will get the best performance is all the vectors are given as StructVectors{<:StaticMatrices{2,2}}.

