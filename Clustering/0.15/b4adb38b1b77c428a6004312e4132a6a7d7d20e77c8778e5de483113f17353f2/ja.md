```
initseeds(alg::Union{SeedingAlgorithm, Symbol},
          X::AbstractMatrix, k::Integer) -> Vector{Int}
```

$$
d×n
$$

データ行列 `X` から `alg` アルゴリズムを使用して `k` 個のシードを選択します。

`alg` は [`SeedingAlgorithm`](@ref) のインスタンスまたはアルゴリズムのシンボリック名のいずれかです。

`k` 個のシードインデックスのベクトルを返します。
