```
==(x::MatrixElem{T}, y::T) where {T <: NCRingElem}
```

Return `true` if $x == S(y)$ arithmetically, where $S$ is the parent of $x$, otherwise return `false`.
