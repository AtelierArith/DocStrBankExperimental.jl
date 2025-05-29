```
is_elementary(T::TorQuadModule, p::Union{Integer, ZZRingElem}) -> Bool
```

Given a torsion quadratic module `T` and a prime number `p`, return whether the underlying (finite) abelian group of `T` (see [`abelian_group`](@ref)) is an elementary `p`-group.
