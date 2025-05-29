```
isequal(x::FracElem{T}, y::FracElem{T}) where {T <: RingElem}
```

Return `true` if $x == y$ exactly, otherwise return `false`. This function is useful in cases where the numerators and denominators of the fractions are inexact, e.g. power series. Only if the power series are precisely the same, to the same precision, are they declared equal by this function.
