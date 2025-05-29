```
==(x::Union{Integer, Rational, AbstractFloat}, y::MatrixElem{T}) where T <: NCRingElement
```

Return `true` if $S(x) == y$ arithmetically, where $S$ is the parent of $y$, otherwise return `false`.
