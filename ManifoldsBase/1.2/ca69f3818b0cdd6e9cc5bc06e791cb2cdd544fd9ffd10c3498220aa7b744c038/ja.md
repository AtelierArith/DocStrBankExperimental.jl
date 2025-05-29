```
vector_transport_to(M::AbstractPowerManifold, p, X, q, method::AbstractVectorTransportMethod)
```

接点 `p` での接ベクトル `X` を [`PowerManifold`](@ref) `M` 上の点 `q` へ、[`AbstractVectorTransportMethod`](@ref) `m` を使用してベクトル輸送を計算します。この方法は要素ごとに実行されるため、方法 `m` は基底多様体上で実装されている必要があります。
