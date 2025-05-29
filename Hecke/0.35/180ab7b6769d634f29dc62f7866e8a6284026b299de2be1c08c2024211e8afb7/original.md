```
is_elementary_with_prime(G::ZZGenus) -> Bool, ZZRingElem
```

Given a genus of $\mathbb Z$-lattices `G`, return whether it is elementary, that is whether the bilinear form is inegtral and the associated discriminant form (see [`discriminant_group`](@ref)) is an elementary `p`-group for some prime number `p`. In case it is, `p` is also returned as second output.

Note that for unimodular genera, this function returns `(true, 1)`. If the genus is not elementary, the second return value is `-1` by default.
