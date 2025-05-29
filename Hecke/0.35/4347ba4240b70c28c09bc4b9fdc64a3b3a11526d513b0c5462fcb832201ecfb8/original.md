```
disc_log(P::EllipticCurvePoint, Q::EllipticCurvePoint, [n::IntegerUnion]) -> ZZRingElem
```

Return the discrete logarithm $m$ of $Q$ with respect to the base $P$, that is, $mP = Q$.

If a multiple $n$ of the order of $P$ is known, this can be supplied as an optional argument.

```jldoctest
julia> E = elliptic_curve(GF(101), [1, 2]);

julia> P = E([6, 74])
(6 : 74 : 1)

julia> Q = E([85, 43])
(85 : 43 : 1)

julia> disc_log(P, Q)
13
```
