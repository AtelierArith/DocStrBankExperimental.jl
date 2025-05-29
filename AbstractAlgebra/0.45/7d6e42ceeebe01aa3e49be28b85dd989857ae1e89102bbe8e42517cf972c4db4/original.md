```
coefficients(a::MPolyRingElem{T}) where T <: RingElement
```

Return an iterator for the coefficients of the given polynomial. To retrieve an array of the coefficients, use `collect(coefficients(a))`.
