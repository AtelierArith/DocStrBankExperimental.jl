```
isequal(x::MatrixElem{T}, y::MatrixElem{T}) where {T <: NCRingElement}
```

Return `true` if $x == y$ exactly, otherwise return `false`. This function is useful in cases where the entries of the matrices are inexact, e.g. power series. Only if the power series are precisely the same, to the same precision, are they declared equal by this function.
