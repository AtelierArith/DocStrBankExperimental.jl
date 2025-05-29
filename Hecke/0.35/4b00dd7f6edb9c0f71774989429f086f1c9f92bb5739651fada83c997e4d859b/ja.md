```
real_places(K::NumField) -> Vector{InfPlc}
```

数体のすべての無限実位を返します。

# 例

```jldoctest
julia> K,  = quadratic_field(5);

julia> infinite_places(K)
2-element Vector{InfPlc{AbsSimpleNumField, AbsSimpleNumFieldEmbedding}}:
 無限位はKの-2.24に対応する複素埋め込みに対応します
 無限位はKの2.24に対応する複素埋め込みに対応します
```
