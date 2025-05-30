```julia
check_density_matrix(ρ; atol, rtol)

```

行列 `ρ` が有効な密度行列であるかどうかを確認します。`atol` と `rtol` は、`ρ` ≈ 1 を確認する際に使用する絶対誤差と相対誤差の許容範囲です。

# 例

```julia-repl
julia> check_density_matrix(σx)
false
julia> check_density_matrix(σi/2)
true
```
