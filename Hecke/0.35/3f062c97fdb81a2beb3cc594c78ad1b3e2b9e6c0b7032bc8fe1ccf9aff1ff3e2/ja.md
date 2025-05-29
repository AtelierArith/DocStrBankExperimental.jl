```
sylow_subgroup(G::FinGenAbGroup, p::IntegerUnion) -> FinGenAbGroup, FinGenAbGroupHom
```

有限生成アーベル群 `G` の Sylow $p-$部分群を返します。ここで、`p` は素数です。これは、`G` の中で `p`-冪の順序を持ち、`G` におけるその指数が `p` と互いに素である部分群です。

# 例

```jldoctest
julia> A = abelian_group(ZZRingElem[2, 6, 30])
Z/2 x Z/6 x Z/30

julia> H, j = sylow_subgroup(A, 2);

julia> H
(Z/2)^3

julia> divexact(order(A), order(H))
45
```
