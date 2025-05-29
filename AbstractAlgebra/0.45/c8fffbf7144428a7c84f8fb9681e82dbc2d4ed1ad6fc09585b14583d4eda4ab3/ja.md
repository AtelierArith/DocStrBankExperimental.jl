```
shift_left(x::AbsPowerSeriesRingElem{T}, n::Int) where T <: RingElement
```

$ x $ を $ n $ 項左にシフトした冪級数を返します。すなわち、$ x^n $ で乗算されます。
