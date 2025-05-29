```
neron_tate_height(P::EllipticCurvePoint{T}, prec::Int) -> ArbFieldElem
  where T<:Union{QQFieldElem, AbsSimpleNumFieldElem}
```

Compute the Néron-Tate height (or canonical height) of a point $P$ on an elliptic curve defined over $\mathbb{Q}$.
