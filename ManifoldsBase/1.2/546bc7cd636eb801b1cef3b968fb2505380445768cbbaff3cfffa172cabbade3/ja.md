```
vector_transport_to(M::ProductManifold, p, X, q, m::AbstractVectorTransportMethod)
```

接続されたベクトル `X` を点 `p` から点 `q` へ [`ProductManifold`](@ref) `M` 上で、各多様体に対して [`AbstractVectorTransportMethod`](@ref) `m` を使用して計算します。
