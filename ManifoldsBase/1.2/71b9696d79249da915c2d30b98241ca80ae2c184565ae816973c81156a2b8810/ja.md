```
vector_transport_direction!(M::AbstractManifold, Y, p, X, d)
vector_transport_direction!(M::AbstractManifold, Y, p, X, d, m::AbstractVectorTransportMethod)
```

点 `p` における [`AbstractManifold`](@ref) `M` の接空間からベクトル `X` を接ベクトル `d` が示す方向に輸送します。デフォルトでは、[`retract`](@ref) と [`vector_transport_to!`](@ref) が `m` と `r` に対して使用され、これらはそれぞれ [`default_vector_transport_method`](@ref)`(M)` と [`default_retraction_method`](@ref)`(M)` にデフォルト設定されています。結果は `Y` に保存されます。

詳細については [`vector_transport_direction`](@ref) を参照してください。
