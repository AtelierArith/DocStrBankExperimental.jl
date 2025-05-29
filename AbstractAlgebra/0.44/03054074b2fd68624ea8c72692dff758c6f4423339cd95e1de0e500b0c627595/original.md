```
exponent_words(a::FreeAssociativeAlgebraElem{T}) where T <: RingElement
```

Return an iterator for the exponent words of the given polynomial. To retrieve an array of the exponent words, use `collect(exponent_words(a))`.
