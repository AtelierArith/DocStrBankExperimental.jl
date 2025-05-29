```
set_coefficient!(c::PolynomialElem{T}, n::Int, a::T) where T <: RingElement
set_coefficient!(c::PolynomialElem{T}, n::Int, a::U) where {T <: RingElement, U <: Integer}
```

次数 $n$ の係数を $a$ に設定します。
