```
isequal(x::AbsPowerSeriesRingElem{T}, y::AbsPowerSeriesRingElem{T}) where T <: RingElement
```

Return `true` if $x == y$ exactly, otherwise return `false`. Only if the power series are precisely the same, to the same precision, are they declared equal by this function.
