```
height_pairing(P::EllipticCurvePoint{T},Q::EllipticCurvePoint{T}, prec::Int)
  -> ArbField where T<:Union{QQFieldElem, AbsSimpleNumFieldElem}
```

2つの点 $P$ と $Q$ の高さペアリングを計算します。これは、$h(P,Q) = (h(P + Q) - h(P) -h(Q))/2$ で定義され、ここで $h$ は標準高さです。
