```
initseeds!(iseeds::AbstractVector{Int}, alg::SeedingAlgorithm,
           X::AbstractMatrix) -> iseeds
```

`iseeds`を`alg`シーディングアルゴリズムを使用して`X`データ行列のクラスタシードのインデックスで初期化します。
