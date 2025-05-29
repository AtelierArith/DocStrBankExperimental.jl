```
image(fs::Vector{Isogeny}, P::EllipticCurvePoint) -> EllipticCurvePoint
```

fsが互換性のあるイソジェニーのリスト[phi*1, ..., phi_n]であるとき、phi*n \circ phi*(n-1) \circ phi*1(P)を返します。
