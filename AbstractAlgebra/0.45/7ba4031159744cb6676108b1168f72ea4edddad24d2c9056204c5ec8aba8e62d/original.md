```
terms(a::MPolyRingElem{T}) where T <: RingElement
```

Return an iterator for the terms of the given polynomial. To retrieve an array of the terms, use `collect(terms(a))`.
