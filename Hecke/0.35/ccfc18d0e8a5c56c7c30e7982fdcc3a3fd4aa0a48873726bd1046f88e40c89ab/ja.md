```
extend(p::InfPlc, L::NumField) -> Vector{InfPlc}
```

数体 `K` の無限位 `p` と `K` の拡張 `L` が与えられたとき、`p` の上にある `L` のすべての無限位を返します。

# 例

```jldoctest
julia> K, a = quadratic_field(3);

julia> L, b = number_field(polynomial(K, [-2, 0, 0, 1]), "b");

julia> p = infinite_places(K)[1];

julia> extend(p, L)
2-element Vector{InfPlc{Hecke.RelSimpleNumField{AbsSimpleNumFieldElem}, RelSimpleNumFieldEmbedding{AbsSimpleNumFieldEmbedding, Hecke.RelSimpleNumField{AbsSimpleNumFieldElem}}}}:
 無限位 (相対数体の根 1.26 に対応する複素埋め込み)
 無限位 (相対数体の根 -0.63 + 1.09 * i に対応する複素埋め込み)
```
