```
height_pairing(P::EllipticCurvePoint{T},Q::EllipticCurvePoint{T}, prec::Int)
  -> ArbField where T<:Union{QQFieldElem, AbsSimpleNumFieldElem}
```

Compute the height pairing of two points $P$ and $Q$ of an elliptic curve defined over a number field. It is defined by $h(P,Q) = (h(P + Q) - h(P) -h(Q))/2$ where $h$ is the canonical height.
