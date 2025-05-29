```
inverse_retract(M::AbstractPowerManifold, p, q, m::AbstractInverseRetractionMethod)
```

点 `q` に関して点 `p` からの逆再tractionを [`AbstractPowerManifold`](@ref) `M` 上で [`AbstractInverseRetractionMethod`](@ref) を使用して計算します。このメソッドは要素ごとに実行されるため、逆再tractionメソッドは基本の [`AbstractManifold`](@ref) で利用可能なものでなければなりません。
