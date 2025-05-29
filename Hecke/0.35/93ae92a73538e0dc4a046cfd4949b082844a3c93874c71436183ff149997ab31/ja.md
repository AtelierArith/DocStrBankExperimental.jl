```
is_elementary(G::ZZGenus, p::Union{Integer, ZZRingElem}) -> Bool
```

整数 $\mathbb Z$-格の属 `G` と素数 `p` が与えられたとき、`G` が `p`-初等であるかどうか、すなわちその関連する判別形式（[`discriminant_group`](@ref) を参照）が初等 `p`-群であるかどうかを返します。
