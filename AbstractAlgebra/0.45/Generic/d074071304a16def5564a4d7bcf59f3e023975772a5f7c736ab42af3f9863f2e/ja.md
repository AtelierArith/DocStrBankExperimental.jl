```
isequal(x::Generic.LaurentSeriesElem{T}, y::Generic.LaurentSeriesElem{T}) where {T <: RingElement}
```

$ x == y $ が正確に等しい場合は `true` を返し、それ以外の場合は `false` を返します。この関数によって等しいと見なされるのは、冪級数が正確に同じで、同じ精度である場合のみです。
