```
==(x::MatrixElem{T}, y::Union{Integer, Rational, AbstractFloat}) where T <: NCRingElement
```

Return `true` if $x == S(y)$ arithmetically, where $S$ is the parent of $x$, otherwise return `false`.
