```
reduced_tate_pairing(P::EllipticCurvePoint, Q::EllipticCurvePoint, n::Int) -> FieldElem
```

有限体 $K$ 上の楕円曲線上の $n$-トーション点 $P$ と別の点 $Q$ が与えられたとき、縮小されたテートペアリング $t_n(P, Q)^{(\#K - 1)/n}$ を返します。

詳細は [`tate_pairing`](@ref) を参照してください。
