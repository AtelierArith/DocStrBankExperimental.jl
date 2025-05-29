```
is_primary(L::ZZLat, p::Union{Integer, ZZRingElem}) -> Bool
```

Given an integral $\mathbb Z$-lattice `L` and a prime number `p`, return whether `L` is `p`-primary, that is whether its discriminant group (see [`discriminant_group`](@ref)) is a `p`-group.
