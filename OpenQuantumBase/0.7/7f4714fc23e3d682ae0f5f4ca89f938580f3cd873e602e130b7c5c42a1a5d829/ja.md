```julia
number_operator(num_levels)

```

`num_levels`で切り捨てられた数演算子を返します。

# 例

```julia-repl
julia> number_operator(3)
3×3 LinearAlgebra.Diagonal{Int64, UnitRange{Int64}}:
 0  ⋅  ⋅
 ⋅  1  ⋅
 ⋅  ⋅  2
```
