```
elliptic_curve(f::PolyRingElem, [h::PolyRingElem,] check::Bool = true) -> EllipticCurve
```

与えられた多項式 $f(x)$ に対して、$y^2 + h(x)y = f(x)$ または $y^2 + y = f(x)$ を返します。$h$ が指定されていない場合は後者が使用されます。多項式 $f$ は次数 3 の単項式でなければならず、$h$ は次数 1 以下でなければなりません。

デフォルトでは、判別式がゼロでないかどうかがチェックされます。これを無効にするには、`check = false` を設定します。

# 例

```jldoctest
julia> Qx, x = QQ["x"];

julia> elliptic_curve(x^3 + x + 1)
Elliptic curve
  over rational field
with equation
  y^2 = x^3 + x + 1

julia> elliptic_curve(x^3 + x + 1, x)
Elliptic curve
  over rational field
with equation
  y^2 + x*y = x^3 + x + 1
```
