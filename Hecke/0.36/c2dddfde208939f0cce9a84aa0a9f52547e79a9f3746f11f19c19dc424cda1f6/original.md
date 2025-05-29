```
is_primary_with_prime(L::ZZLat) -> Bool, ZZRingElem
```

Given a $\mathbb Z$-lattice `L`, return whether `L` is primary, that is whether `L` is integral and its discriminant group (see [`discriminant_group`](@ref)) is a `p`-group for some prime number `p`. In case it is, `p` is also returned as second output.

Note that for unimodular lattices, this function returns `(true, 1)`. If the lattice is not primary, the second return value is `-1` by default.
