```
UncertainValue(empiricaldata::AbstractVector{T},
    d::Type{D}) where {D <: Distribution}
```

# Constructor for empirical distributions.

Fit a distribution of type `d` to the data and use that as the representation of the empirical distribution. Calls `Distributions.fit` behind the scenes.

## Arguments

  * **`empiricaldata`**: The data for which to fit the `distribution`.
  * **`distribution`**: A valid univariate distribution from `Distributions.jl`.
