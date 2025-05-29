```
embeddings(p::InfPlc) -> Vector{NumFieldEmb}
```

複素数体を与えると、この体を定義するすべての複素埋め込みを返します。

関連情報として [`embedding`](@ref) を参照してください。

# 例

```jldoctest
julia> K,  = quadratic_field(-5);

julia> embeddings(complex_places(K)[1])
2-element Vector{AbsSimpleNumFieldEmbedding}:
 Imaginary embedding with 0.00 + 2.24 * i of K
 Imaginary embedding with 0.00 - 2.24 * i of K
```
