```julia
number_operator(num_levels)

```

Return the number operator truncated at `num_levels`.

# Examples

```julia-repl
julia> number_operator(3)
3×3 LinearAlgebra.Diagonal{Int64, UnitRange{Int64}}:
 0  ⋅  ⋅
 ⋅  1  ⋅
 ⋅  ⋅  2
```
