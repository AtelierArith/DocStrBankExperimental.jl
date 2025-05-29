```
monomials(a::MPolyRingElem{T}) where T <: RingElement
```

Return an iterator for the monomials of the given polynomial. To retrieve an array of the monomials, use `collect(monomials(a))`.
