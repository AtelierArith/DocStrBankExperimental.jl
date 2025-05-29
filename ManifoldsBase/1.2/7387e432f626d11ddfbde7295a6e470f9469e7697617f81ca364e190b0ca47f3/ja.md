```
retract(M::ProductManifold, p, X, m::ProductRetraction)
```

[`ProductManifold`](@ref) `M` 上の点 `p` から接ベクトル `X` を用いて [`ProductRetraction`](@ref) による再tractionを計算します。デフォルトでは、基底多様体の再tractionをカプセル化します。このメソッドは要素ごとに実行されるため、カプセル化された再tractionメソッドは多様体上で利用可能なものでなければなりません。
