```
==(x::T, y::MatrixElem{T}) where {T <: NCRingElem}
```

Return `true` if $S(x) == y$ arithmetically, where $S$ is the parent of $y$, otherwise return `false`.
