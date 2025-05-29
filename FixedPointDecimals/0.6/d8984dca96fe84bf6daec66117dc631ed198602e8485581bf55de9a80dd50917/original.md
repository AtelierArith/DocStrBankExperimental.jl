```
div_with_overflow(x::FixedDecimal{T,f}, y::FixedDecimal{T,f})::(FixedDecimal{T,f}, Bool)
    where {T<:Integer, f}
```

Return the result of div (wrapping on overflow/underflow) and a boolean indicating whether overflow/underflow did in fact happen. Throws a DivideError on divide-by-zero.
