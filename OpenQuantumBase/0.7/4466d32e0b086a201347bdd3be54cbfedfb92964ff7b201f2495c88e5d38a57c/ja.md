```julia
annihilation_operator(num_levels)

```

`num_levels` で切り捨てられた消滅演算子を返します。

# 例

```julia-repl
julia> annihilation_operator(3)
3×3 LinearAlgebra.Bidiagonal{Float64, Vector{Float64}}:
 0.0  1.0   ⋅
  ⋅   0.0  1.41421
  ⋅    ⋅   0.0
```
