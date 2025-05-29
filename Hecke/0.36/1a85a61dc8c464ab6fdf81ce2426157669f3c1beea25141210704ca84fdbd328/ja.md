```
height_pairing(P::EllipticCurvePoint{T},Q::EllipticCurvePoint{T}, prec::Int)
  -> ArbField where T<:Union{QQFieldElem, AbsSimpleNumFieldElem}
```

2つの点 $P$ と $Q$ の高さペアリングを計算します。これは、数体上で定義された楕円曲線の高さ $h(P,Q) = (h(P + Q) - h(P) -h(Q))/2$ によって定義されます。ここで、$h$ は標準高さです。
