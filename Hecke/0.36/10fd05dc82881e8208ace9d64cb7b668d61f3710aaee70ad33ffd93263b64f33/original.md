```
transform_rstu(E::EllipticCurve, [r, s, t, u]::Vector{T})
-> EllipticCurve, EllCrvIso, EllCrvIso
```

Return the transformation of E under the isomorphism given by [(x - r)//u^2 : (y - s*(x-r) - t)//u^3 : 1], the isomorphism and the inverse of the isomorphism
