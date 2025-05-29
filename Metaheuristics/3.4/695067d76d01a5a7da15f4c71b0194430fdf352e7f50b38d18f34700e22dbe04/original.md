```
Grid(npartitions, dim)
```

Parameters to generate a grid with `npartitions` in a space with `dim` dimensions.

### Example

```julia-repl
julia> sample(Grid(5,2))
25×2 Matrix{Float64}:
 0.0   0.0
 0.25  0.0
 0.5   0.0
 0.75  0.0
 ⋮     
 0.5   1.0
 0.75  1.0
 1.0   1.0

julia> sample(Grid(5,2), [-1 -1; 1 1.])
25×2 Matrix{Float64}:
 -1.0  -1.0
 -0.5  -1.0
  0.0  -1.0
  0.5  -1.0
  ⋮    
  0.0   1.0
  0.5   1.0
  1.0   1.0
```

Note that the sample is with size `npartitions^(dim)`.
