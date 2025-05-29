```
fgt(v, w, α, z)
```

Compute the Foster–Greer–Thorbecke Index of a vector `v` at a specified `α` and  a given poverty threshold `z`, using weights given by a weight vector `w`.

Weights must not be negative, missing or NaN. The weights and data vectors must have the same length.

# Examples

```julia
julia> using Inequality
julia> fgt([8, 5, 1, 3, 5, 6, 7, 6, 3], collect(0.1:0.1:0.9), 2, 4)
0.05555555555555555
```
