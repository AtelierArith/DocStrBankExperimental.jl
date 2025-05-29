```
equation([R::MPolyRing,] E::EllipticCurve) -> MPolyRingElem
```

楕円曲線 $E$ を二変数多項式として定義する方程式を返します。多項式環 $R$ が指定されている場合、それは二変数多項式環でなければなりません。

# 例

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2, 3, 4, 5]);

julia> equation(E)
-x^3 - 2*x^2 + x*y - 4*x + y^2 + 3*y - 5
```
