```
isequal(x::PolyRingElem{T}, y::PolyRingElem{T}) where T <: RingElement
```

Return `true` if $x == y$ exactly, otherwise return `false`. This function is useful in cases where the coefficients of the polynomial are inexact, e.g. power series. Only if the power series are precisely the same, to the same precision, are they declared equal by this function.
