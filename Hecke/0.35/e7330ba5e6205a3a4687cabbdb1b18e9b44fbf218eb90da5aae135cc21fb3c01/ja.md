```
complex_embeddings(K::NumField; conjugates::Bool = true) -> Vector{NumFieldEmb}
```

$$
K
$$

の複素埋め込みを返します。`conjugates`が`false`の場合、共役ペアごとに1つの虚数埋め込みのみが返されます。

# 例

```jldoctest
julia> K, a = quadratic_field(-3);

julia> complex_embeddings(K)
2-element Vector{AbsSimpleNumFieldEmbedding}:
 Kの0.00 + 1.73 * iに対応する複素埋め込み
 Kの0.00 - 1.73 * iに対応する複素埋め込み

julia> complex_embeddings(K, conjugates = false)
1-element Vector{AbsSimpleNumFieldEmbedding}:
 Kの0.00 + 1.73 * iに対応する複素埋め込み
```
