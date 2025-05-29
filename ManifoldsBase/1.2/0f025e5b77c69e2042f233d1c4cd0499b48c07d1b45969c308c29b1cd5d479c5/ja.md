```
vector_transport_to(M::AbstractManifold, p, X, q)
vector_transport_to(M::AbstractManifold, p, X, q, m::AbstractVectorTransportMethod)
vector_transport_to(M::AbstractManifold, p, X, q, m::AbstractVectorTransportMethod)
```

点 `p` における接空間からベクトル `X` を、`m` に関連付けられた [`AbstractRetractionMethod`](@ref) によって暗黙的に与えられた曲線に沿って [`AbstractManifold`](@ref) `M` の点 `q` へ輸送します。デフォルトでは、`m` は [`default_vector_transport_method`](@ref)`(M)` です。暗黙的に仮定された再tractionとは異なる再tractionを明示的に指定するには、[`VectorTransportTo`](@ref) を参照してください。一部のベクトル輸送法は、[`DifferentiatedRetractionVectorTransport`](@ref) のように、関連付けられた独自の再tractionを持つ場合があります。また、[`ProjectionTransport`](@ref) のように再tractionに依存しないものもあります。

このメソッドは、[`vector_transport_direction`](@ref)`(M, p, X, q, m, r)` において $d = \operatorname{retr}^{-1}_p(q)$ を使用することと同等であり、正式な定義を見つけることができます。これは [`VectorTransportTo`](@ref) のフォールバックです。
