```
reduced_tate_pairing(P::EllipticCurvePoint, Q::EllipticCurvePoint, n::Int) -> FieldElem
```

$$
n
$$

-トーション点$P$と有限体$K$上の他の点$Q$が与えられたとき、縮小されたテートペアリング$t_n(P, Q)^{(\#K - 1)/n}$を返します。

[`tate_pairing`](@ref)も参照してください。
