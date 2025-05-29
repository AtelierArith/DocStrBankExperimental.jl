```
is_primary_with_prime(T::TorQuadModule) -> Bool, ZZRingElem
```

Given a torsion quadratic module `T`, return whether the underlying (finite) abelian group of `T` (see [`abelian_group`](@ref)) is a `p`-group for some prime number `p`. In case it is, `p` is also returned as second output.

Note that in the case of trivial groups, this function returns `(true, 1)`. If `T` is not primary, the second return value is `-1` by default.
