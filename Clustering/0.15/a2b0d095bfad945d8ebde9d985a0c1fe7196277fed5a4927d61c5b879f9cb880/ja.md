```
initseeds_by_costs!(iseeds::AbstractVector{Int}, alg::SeedingAlgorithm,
                    costs::AbstractMatrix) -> iseeds
```

`iseeds`を`alg`シーディングアルゴリズムを使用して`costs`行列のクラスタシードのインデックスで初期化します。

ここで、`costs[i, j]`は、点$i$と$j$を同じクラスタに割り当てるコストです。例えば、コストとして点間の二乗ユークリッド距離を使用することができます。
