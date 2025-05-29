```
is_elementary(G::ZZGenus, p::Union{Integer, ZZRingElem}) -> Bool
```

Given a genus of integral $\mathbb Z$-lattices `G` and a prime number `p`, return whether `G` is `p`-elementary, that is whether its associated discriminant form (see [`discriminant_group`](@ref)) is an elementary `p`-group.
