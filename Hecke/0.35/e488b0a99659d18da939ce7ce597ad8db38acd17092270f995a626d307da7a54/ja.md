```
real_embeddings(K::NumField) -> Vector{NumFieldEmb}
```

$$
K
$$

の実埋め込みを返します。

# 例

```jldoctest
julia> K, a = quadratic_field(3);

julia> real_embeddings(K)
2-element Vector{AbsSimpleNumFieldEmbedding}:
 Kの-1.73に対応する複素埋め込み
 Kの1.73に対応する複素埋め込み
```
