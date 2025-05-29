```
exponent_vectors(a::MPolyRingElem{T}) where T <: RingElement
```

Return an iterator for the exponent vectors of the given polynomial. To retrieve an array of the exponent vectors, use `collect(exponent_vectors(a))`.
