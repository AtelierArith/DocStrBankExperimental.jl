```
pseudorem(f::PolyRingElem{T}, g::PolyRingElem{T}) where T <: RingElement
```

Return the pseudoremainder of $f$ divided by $g$. If $g = 0$ we throw a `DivideError()`.
