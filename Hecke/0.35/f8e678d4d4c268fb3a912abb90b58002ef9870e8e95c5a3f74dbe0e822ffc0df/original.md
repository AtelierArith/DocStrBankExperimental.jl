```
hasse_interval(E::EllipticCurve) -> (ZZRingElem, ZZRingElem)
```

Given an elliptic curve $E$ over a finite field $\mathbf F$, return an array `[l, b]` of integers, such that $l \leq \#E(\mathbf F) \leq b$ using Hasse's theorem.

# Examples

```jldoctest
julia> E = elliptic_curve(GF(3), [1, 2]);

julia> hasse_interval(E)
(0, 8)
```
