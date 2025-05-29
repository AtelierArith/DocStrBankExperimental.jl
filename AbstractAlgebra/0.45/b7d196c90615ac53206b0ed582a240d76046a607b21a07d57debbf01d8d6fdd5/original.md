```
==(x::NCPolyRingElem{T}, y::NCPolyRingElem{T}) where T <: NCRingElem
```

Return `true` if $x == y$ arithmetically, otherwise return `false`. Recall that power series to different precisions may still be arithmetically equal to the minimum of the two precisions.
