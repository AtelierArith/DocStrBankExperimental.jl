```
initseeds_by_costs(alg::Union{SeedingAlgorithm, Symbol},
                   costs::AbstractMatrix, k::Integer) -> Vector{Int}
```

アルゴリズム `alg` を使用して、$n×n$ `costs` 行列から `k` 個のシードを選択します。

ここで、`costs[i, j]` は、ポイント `i` と `j` を同じクラスタに割り当てるコストです。たとえば、コストとしてポイント間の二乗ユークリッド距離を使用することができます。

`k` 個のシードインデックスのベクターを返します。
