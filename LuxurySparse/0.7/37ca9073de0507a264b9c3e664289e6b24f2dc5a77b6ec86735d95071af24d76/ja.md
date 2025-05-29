```
pmrand(T::Type, n::Int) -> PermMatrix
```

型 `T` の `n` 行 `n` 列のランダムな [`PermMatrix`](@ref) を返します。

# 例

```julia-repl
julia> pmrand(ComplexF64, 4)
4×4 SDPermMatrix{ComplexF64, Int64, Vector{ComplexF64}, Vector{Int64}}:
        0.0+0.0im      0.112104+0.0179632im       0.0+0.0im              0.0+0.0im
 -0.0625997+1.00664im       0.0+0.0im             0.0+0.0im              0.0+0.0im
        0.0+0.0im           0.0+0.0im             0.0+0.0im       -0.0981836-0.839471im
        0.0+0.0im           0.0+0.0im        0.735853-0.747084im         0.0+0.0im

```
