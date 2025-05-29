```
theil(v, w)
```

Compute the Theil Index of a vector `v`, using weights given by a weight vector `w`.

Weights must not be negative, missing or NaN. The weights and data vectors must have the same length.

# Examples

```julia
julia> using Inequality
julia> theil([8, 5, 1, 3, 5, 6, 7, 6, 3], collect(0.1:0.1:0.9))
0.08120013911680612
```
