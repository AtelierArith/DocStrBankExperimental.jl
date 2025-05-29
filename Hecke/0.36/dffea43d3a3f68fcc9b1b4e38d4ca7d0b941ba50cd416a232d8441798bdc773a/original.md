```
regulator(u::Vector{T}, C::qAdicConj, n::Int = 10; flat::Bool = true) where {T<: Union{AbsSimpleNumFieldElem, FacElem{AbsSimpleNumFieldElem, AbsSimpleNumField}}}
regulator(K::AbsSimpleNumField, C::qAdicConj, n::Int = 10; flat::Bool = true)
regulator(R::AbsNumFieldOrder, C::qAdicConj, n::Int = 10; flat::Bool = true)
```

Returns the determinant of $m^t m$ where the columns of $m$ are the `conjugates_log` of the units in either the array, or the fundamental units for $K$ (the maximal order of $K$) or $R$. If `flat = false`, then all prime ideals over $p$ need to have the same degree. In either case, Leopold's conjecture states that the regulator is zero iff the units are dependent.
