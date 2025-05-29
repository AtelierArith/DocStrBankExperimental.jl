```
neron_tate_height(P::EllipticCurvePoint{T}, prec::Int) -> ArbFieldElem
  where T<:Union{QQFieldElem, AbsSimpleNumFieldElem}
```

点 $P$ の Néron-Tate 高さ（または標準高）を計算します。$P$ は $\mathbb{Q}$ 上で定義された楕円曲線上の点です。
