```
pseudodivrem(f::PolyRingElem{T}, g::PolyRingElem{T}) where T <: RingElement
```

Return a tuple $(q, r)$ consisting of the pseudoquotient and pseudoremainder of $f$ divided by $g$. If $g = 0$ we throw a `DivideError()`.
