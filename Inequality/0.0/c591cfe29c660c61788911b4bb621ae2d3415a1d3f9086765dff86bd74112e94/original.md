```
atkinson(v, w, ϵ)
```

Compute the weighted Atkinson Index of a vector `v` at a specified inequality  aversion parameter `ϵ`, using weights given by a weight vector `w`.

Weights must not be negative, missing or NaN. The weights and data vectors must have the same length.

# Examples

```julia
julia> using Inequality
julia> atkinson([8, 5, 1, 3], [0.1,0.5,0.3,0.8], 1.2)
0.1681319821792493
```
