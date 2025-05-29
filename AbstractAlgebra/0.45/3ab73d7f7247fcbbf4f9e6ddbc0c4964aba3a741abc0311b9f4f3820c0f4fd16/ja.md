```
shift_right(x::AbsPowerSeriesRingElem{T}, n::Int) where T <: RingElement
```

$ x $ を $ n $ 項右にシフトした冪級数を返します。すなわち、$ x^n $ で割ります。
