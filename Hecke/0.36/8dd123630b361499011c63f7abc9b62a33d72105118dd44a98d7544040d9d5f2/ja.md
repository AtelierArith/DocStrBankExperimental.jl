```
complex_places(K::NumField) -> Vector{InfPlc}
```

$$
K
$$

のすべての無限複素位を返します。

# 例

```jldoctest
julia> K,  = quadratic_field(-5);

julia> complex_places(K)
1-element Vector{InfPlc{AbsSimpleNumField, AbsSimpleNumFieldEmbedding}}:
 Kの0.00 + 2.24 * iの虚数埋め込みを持つ無限位
```
