```
isomorphism(E::EllipticCurve, [r, s, t, u]::Vector{T}) -> EllCrvIso
```

Return the isomorphism with domain E given by [(x - r)//u^2 : (y - s*(x-r) - t)//u^3 : 1]. The codomain is calculated automatically.
