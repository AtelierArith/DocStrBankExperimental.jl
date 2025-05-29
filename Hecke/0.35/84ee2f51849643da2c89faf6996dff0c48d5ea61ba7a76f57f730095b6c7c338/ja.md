```
elliptic_curve([K::Field], x::Vector; check::Bool = true) -> EllipticCurve
```

Weierstrass 方程式によって指定された係数 `x` を持つ楕円曲線を構築します。`x` の長さは 2 または 5 でなければなりません。

デフォルトでは、判別式がゼロでないかどうかがチェックされます。これを無効にするには、`check = false` に設定します。

# 例

```jldoctest
julia> elliptic_curve(QQ, [1, 2, 3, 4, 5])
Elliptic curve
  over rational field
with equation
  y^2 + x*y + 3*y = x^3 + 2*x^2 + 4*x + 5

julia> elliptic_curve(GF(3), [1, 1])
Elliptic curve
  over prime field of characteristic 3
with equation
  y^2 = x^3 + x + 1
```
