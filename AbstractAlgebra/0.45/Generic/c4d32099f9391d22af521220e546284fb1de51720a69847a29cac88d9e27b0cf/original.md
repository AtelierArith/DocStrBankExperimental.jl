```
shift_right(x::Generic.LaurentSeriesElem{T}, n::Int) where {T <: RingElement}
```

Return the power series $x$ shifted right by $n$ terms, i.e. divided by $x^n$.
