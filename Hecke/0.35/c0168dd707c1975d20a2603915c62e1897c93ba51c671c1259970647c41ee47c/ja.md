```
rescale(L::ZZLat, r::RationalUnion) -> ZZLat
```

二次形式 `r \Phi` を持つ格子 `L` を返します。

# 例

これは、正定値格子向けに設計されたメソッドを適用するのに役立ちます。

```jldoctest
julia> L = integer_lattice(gram=ZZ[-1 0; 0 -1])
階数 2 および次数 2 の整数格子
グラム行列
[-1    0]
[ 0   -1]

julia> shortest_vectors(rescale(L, -1))
2-element Vector{Vector{ZZRingElem}}:
 [0, 1]
 [1, 0]
```
