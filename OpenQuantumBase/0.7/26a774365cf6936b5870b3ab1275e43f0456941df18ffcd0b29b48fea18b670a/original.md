```julia
creation_operator(num_levels)

```

Return the creation operator truncated at `num_levels`.

# Examples

```julia-repl
julia> creation_operator(3)
3×3 LinearAlgebra.Bidiagonal{Float64, Vector{Float64}}:
 0.0   ⋅        ⋅ 
 1.0  0.0       ⋅
  ⋅   1.41421  0.0
```
