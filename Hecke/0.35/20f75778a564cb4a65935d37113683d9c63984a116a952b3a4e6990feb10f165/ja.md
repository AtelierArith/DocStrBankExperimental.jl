```
isomorphism(E::EllipticCurve, [r, s, t, u]::Vector{T}) -> EllCrvIso
```

与えられた E の定義域を持つ同型を返します。[(x - r)//u^2 : (y - s*(x-r) - t)//u^3 : 1] によって定義されます。コドメインは自動的に計算されます。
