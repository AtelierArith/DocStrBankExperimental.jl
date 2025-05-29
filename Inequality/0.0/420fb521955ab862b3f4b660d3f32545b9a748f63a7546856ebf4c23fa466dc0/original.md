```
watts(v, k)

Compute the Watts Poverty Index of a vector `v` at a specified absolute 
poverty line `k`.
```

# Examples

```julia
julia> using Inequality
julia> watts([8, 5, 1, 3, 5, 6, 7, 6, 3], 4)
0.217962056224828
```
