```
local_correlation_dimension(X, ζ [, εs]; kw...) → Δ_ζ
```

Return the local dimension `Δ_ζ` around state space point `ζ` given a set of state space points `X` which is assumed to surround (or be sufficiently near to) `ζ`. The local dimension is the exponential scaling of the correlation sum for point `ζ` versus some radii `εs`. `εs` can be a vector of reals, or it can be an integer, in which space that many points are equi-spaced logarithmically between the minimum and maximum distance of `X` to `ζ`.

## Keyword arguments

  * `q = 2, norm = Euclidean()`: same as in [`correlationsum`](@ref).
  * `fit = LinearRegression()`: given to [`slopefit`](@ref) to estimate the dimension. This default assumes that the set `X` is already sufficiently close to `ζ`.
