```
isequal(a::ResFieldElem{T}, b::ResFieldElem{T}) where {T <: RingElement}
```

Return `true` if $a == b$ exactly, otherwise return `false`. This function is useful in cases where the data of the residues are inexact, e.g. power series Only if the power series are precisely the same, to the same precision, are they declared equal by this function.
