```
coeff(f::MPolyRingElem{T}, m::MPolyRingElem{T}) where T <: RingElement
```

Return the coefficient of the monomial $m$ of the polynomial $f$. If there is no such monomial, zero is returned.
