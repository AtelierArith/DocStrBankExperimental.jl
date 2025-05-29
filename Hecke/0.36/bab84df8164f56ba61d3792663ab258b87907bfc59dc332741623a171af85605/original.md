```
is_primary(G::ZZGenus, p::Union{Integer, ZZRingElem}) -> Bool
```

Given a genus of integral $\mathbb Z$-lattices `G` and a prime number `p`, return whether `G` is `p`-primary, that is whether the associated discriminant form (see [`discriminant_group`](@ref)) is a `p`-group.
