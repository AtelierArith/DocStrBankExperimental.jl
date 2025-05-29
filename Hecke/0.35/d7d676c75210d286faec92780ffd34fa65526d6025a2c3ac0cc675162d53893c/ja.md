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
 無限位 (Kの0.00 + 2.24 * iに対応する複素埋め込みに対応)
```
