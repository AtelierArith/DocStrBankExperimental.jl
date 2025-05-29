```
watts(v, w, α)
```

Compute the Watts Poverty Index of a vector `v` at a specified absolute  poverty line `α`, using weights given by a weight vector `w`.

Weights must not be negative, missing or NaN. The weights and data vectors must have the same length.

# Examples

```julia
julia> using Inequality
julia> watts([8, 5, 1, 3, 5, 6, 7, 6, 3], collect(0.1:0.1:0.9), 4)
0.17552777833850716
```
