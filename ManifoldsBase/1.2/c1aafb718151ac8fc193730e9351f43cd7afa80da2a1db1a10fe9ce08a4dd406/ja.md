```
vector_transport_to!(M::AbstractManifold, Y, p, X, q)
vector_transport_to!(M::AbstractManifold, Y, p, X, q, m::AbstractVectorTransportMethod)
```

点 `p` における接空間からベクトル `X` を [`AbstractManifold`](@ref) `M` の `q` へ、[`AbstractVectorTransportMethod`](@ref) `m` と [`AbstractRetractionMethod`](@ref) `r` を使用して輸送します。

結果は `Y` で計算されます。詳細については [`vector_transport_to`](@ref) を参照してください。
