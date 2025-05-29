```
tate_pairing(P::EllipticCurvePoint{T}, Q::EllipticCurvePoint{T}, n::Int) where T
```

Given an $n$-torsion point $P$ and another point $Q$ on an elliptic curve over a finite field $K$. Return the Tate pairing $t_n(P, Q)$ by returning a representative of the coset modulo $n$-th powers.

See also [reduced*tate*pairing](@ref) if one wants an $n$-th root.
