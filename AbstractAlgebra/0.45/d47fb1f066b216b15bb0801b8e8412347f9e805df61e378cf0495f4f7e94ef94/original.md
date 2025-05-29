```
==(x::RelPowerSeriesRingElem{T}, y::RelPowerSeriesRingElem{T}) where T <: RingElement
```

Return `true` if $x == y$ arithmetically, otherwise return `false`. Recall that power series to different precisions may still be arithmetically equal to the minimum of the two precisions.
