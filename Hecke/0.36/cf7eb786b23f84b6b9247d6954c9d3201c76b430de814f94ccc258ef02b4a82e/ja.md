```
real_places(K::NumField) -> Vector{InfPlc}
```

数体のすべての無限実位を返します。

# 例

```jldoctest
julia> K,  = quadratic_field(5);

julia> infinite_places(K)
2-element Vector{InfPlc{AbsSimpleNumField, AbsSimpleNumFieldEmbedding}}:
 Kの-2.24の実埋め込みの無限位
 Kの2.24の実埋め込みの無限位
```
