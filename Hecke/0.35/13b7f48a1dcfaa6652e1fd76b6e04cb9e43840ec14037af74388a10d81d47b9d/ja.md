```
elliptic_curve_from_j_invariant(j::FieldElem) -> EllipticCurve
```

与えられた $j$-不変量を持つ楕円曲線を返します。

# 例

```jldoctest
julia> K = GF(3)
特性 3 の素体

julia> elliptic_curve_from_j_invariant(K(2))
楕円曲線
  特性 3 の素体上
方程式
  y^2 + x*y = x^3 + 1
```
