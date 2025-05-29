```
map_entries!(f, dst::MatrixElem{T}, src::MatrixElem{U}) where {T <: NCRingElement, U <: NCRingElement}
```

Like `map_entries`, but stores the result in `dst` rather than a new matrix.
