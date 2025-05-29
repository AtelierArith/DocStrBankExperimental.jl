```
set_coefficient!(c::PolynomialElem{T}, n::Int, a::T) where T <: RingElement
set_coefficient!(c::PolynomialElem{T}, n::Int, a::U) where {T <: RingElement, U <: Integer}
```

Set the coefficient of degree $n$ to $a$.
