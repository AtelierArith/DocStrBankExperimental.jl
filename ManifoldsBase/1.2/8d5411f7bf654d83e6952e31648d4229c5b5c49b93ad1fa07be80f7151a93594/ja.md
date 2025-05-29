```
retract(M::AbstractPowerManifold, p, X, method::AbstractRetractionMethod)
```

点 `p` から接ベクトル `X` を用いて [`AbstractPowerManifold`](@ref) `M` 上で再収束を計算します。このメソッドは要素ごとに実行されるため、再収束メソッドは基本の [`AbstractManifold`](@ref) で利用可能なものでなければなりません。
