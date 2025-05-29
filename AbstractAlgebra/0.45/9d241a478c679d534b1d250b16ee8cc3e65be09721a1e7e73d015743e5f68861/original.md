```
==(x::MatrixElem{T}, y::MatrixElem{T}) where {T <: NCRingElement}
```

Return `true` if $x == y$ arithmetically, otherwise return `false`. Recall that power series to different precisions may still be arithmetically equal to the minimum of the two precisions.
