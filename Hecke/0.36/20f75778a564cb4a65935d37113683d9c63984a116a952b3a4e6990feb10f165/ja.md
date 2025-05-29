```
isomorphism(E::EllipticCurve, [r, s, t, u]::Vector{T}) -> EllCrvIso
```

ドメイン E に対する同型を返します。これは [(x - r)//u^2 : (y - s*(x-r) - t)//u^3 : 1] によって与えられます。コドメインは自動的に計算されます。
