```
order(P::EllipticCurvePoint, [fac::Fac{ZZRingElem}]) -> ZZRingElem
```

Given a point $P$ on an elliptic curve $E$ over a finite field, return the order of this point.

Optionally, one can supply the factorization of a multiple of the point order, for example the order of $E$.

# Examples

```jldoctest
julia> E = elliptic_curve(GF(101), [1, 2]);

julia> P = E([17, 65]);

julia> order(P)
100

julia> fac = factor(order(E))
1 * 5^2 * 2^2

julia> order(P, fac)
100
```
