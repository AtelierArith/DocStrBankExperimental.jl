```
embeddings(p::InfPlc) -> Vector{NumFieldEmb}
```

複素位相を与えると、この位相を定義するすべての複素埋め込みを返します。

参照: [`embedding`](@ref).

# 例

```jldoctest
julia> K,  = quadratic_field(-5);

julia> embeddings(complex_places(K)[1])
2-element Vector{AbsSimpleNumFieldEmbedding}:
 Kの0.00 + 2.24 * iに対応する複素埋め込み
 Kの0.00 - 2.24 * iに対応する複素埋め込み
```
