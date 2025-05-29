```
gini(v, w)
```

Compute the weighted Gini Coefficient of a vector `v` using weights given by a weight vector `w`.

Weights must not be negative, missing or NaN. The weights and data vectors must have the same length.

# Examples

```julia
julia> using Inequality
julia> gini([8, 5, 1, 3, 5, 6, 7, 6, 3], collect(0.1:0.1:0.9))
0.20652395514780775
```
