```
shift_right(x::AbsPowerSeriesRingElem{T}, n::Int) where T <: RingElement
```

冪級数 $x$ を $n$ 項右にシフトしたものを返します。すなわち、$x^n$ で割ったものです。
