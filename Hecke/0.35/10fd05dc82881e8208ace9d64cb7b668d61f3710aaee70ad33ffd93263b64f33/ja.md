```
transform_rstu(E::EllipticCurve, [r, s, t, u]::Vector{T})
-> EllipticCurve, EllCrvIso, EllCrvIso
```

Eの変換を返します。変換は[(x - r)//u^2 : (y - s*(x-r) - t)//u^3 : 1]によって与えられる同型、同型、および同型の逆です。
