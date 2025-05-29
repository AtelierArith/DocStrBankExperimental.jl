```
predict(M::SpatialPCA, x::AbstractVecOrMat{<:Real})
```

Transform the observations `x` with the SpatialPCA model `M`.

Here, `x` can be either a vector of length `d` or a matrix where each column is an observation.
