```
==(a::ResFieldElem{T}, b::ResFieldElem{T}) where {T <: RingElement}
```

Return `true` if $a == b$ arithmetically, otherwise return `false`. Recall that power series to different precisions may still be arithmetically equal to the minimum of the two precisions.
