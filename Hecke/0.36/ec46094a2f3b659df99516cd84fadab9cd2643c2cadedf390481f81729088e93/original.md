```
local_height(P::EllipticCurvePoint{QQFieldElem}, p::IntegerUnion, prec::Int) -> ArbField
```

Computes the local height of a point $P$ on an elliptic curve defined over $\mathbf{Q}$ at $p$. The number $p$ must be a prime or $0$. In the latter case, the height at the infinite place is returned.
