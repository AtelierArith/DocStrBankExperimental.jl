```
infinite_places(K::NumField) -> Vector{InfPlc}
```

数体のすべての無限位を返します。

# 例

```jldoctest
julia> K,  = quadratic_field(5);

julia> infinite_places(K)
2-element Vector{InfPlc{AbsSimpleNumField, AbsSimpleNumFieldEmbedding}}:
 Kの実埋め込みによる無限位 -2.24
 Kの実埋め込みによる無限位 2.24
```
