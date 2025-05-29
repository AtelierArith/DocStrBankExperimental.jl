```
is_primary(L::ZZLat, p::Union{Integer, ZZRingElem}) -> Bool
```

与えられた整数 $\mathbb Z$-格 `L` と素数 `p` に対して、`L` が `p`-主であるかどうか、すなわちその判別群（[`discriminant_group`](@ref）を参照） が `p`-群であるかどうかを返します。
