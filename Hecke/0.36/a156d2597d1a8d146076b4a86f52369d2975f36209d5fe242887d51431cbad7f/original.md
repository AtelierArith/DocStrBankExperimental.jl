```
reduced_tate_pairing(P::EllipticCurvePoint, Q::EllipticCurvePoint, n::Int) -> FieldElem
```

Given an $n$-torsion point $P$ and another point $Q$ on an elliptic curve over a finite field $K$, eturn the reduced Tate pairing $t_n(P, Q)^{(\#K - 1)/n}$.

See also [`tate_pairing`](@ref).
