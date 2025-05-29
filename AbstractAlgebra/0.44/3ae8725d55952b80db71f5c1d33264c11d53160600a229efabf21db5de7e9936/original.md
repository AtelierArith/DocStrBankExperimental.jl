```
isempty(a::MatrixElem{T}) where T <: NCRingElement
```

Return `true` if `a` does not contain any entry (i.e. `length(a) == 0`), and `false` otherwise.
