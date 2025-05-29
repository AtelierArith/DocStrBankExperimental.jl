```
shift_left(x::Generic.LaurentSeriesElem{T}, n::Int) where {T <: RingElement}
```

Return the power series $x$ shifted left by $n$ terms, i.e. multiplied by $x^n$.
