```
elliptic_curve(f::PolyRingElem, [h::PolyRingElem,] check::Bool = true) -> EllipticCurve
```

指定された場合、楕円曲線 $y^2 + h(x)y = f(x)$ を返します。指定されない場合は $y^2 + y = f(x)$ になります。多項式 $f$ は次数3の単項式でなければならず、$h$ は次数1以下でなければなりません。

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
