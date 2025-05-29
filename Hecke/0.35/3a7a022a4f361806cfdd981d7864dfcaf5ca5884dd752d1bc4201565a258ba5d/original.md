```
is_elementary(L::ZZLat, p::Union{Integer, ZZRingElem}) -> Bool
```

Given an integral $\mathbb Z$-lattice `L` and a prime number `p`, return whether `L` is `p`-elementary, that is whether its discriminant group (see [`discriminant_group`](@ref)) is an elementary `p`-group.
