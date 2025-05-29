```
is_primary(G::ZZGenus, p::Union{Integer, ZZRingElem}) -> Bool
```

整数 $\mathbb Z$-格子の属する族 `G` と素数 `p` が与えられたとき、`G` が `p`-主であるかどうか、すなわち関連する判別形式（[`discriminant_group`](@ref) を参照） が `p`-群であるかどうかを返します。
