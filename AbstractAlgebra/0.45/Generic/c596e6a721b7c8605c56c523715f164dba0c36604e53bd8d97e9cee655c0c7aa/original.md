```
normal_form(p::U, I::Ideal{U}) where {T <: RingElement, U <: Union{AbstractAlgebra.PolyRingElem{T}, AbstractAlgebra.MPolyRingElem{T}}}
```

Return the normal form of the polynomial `p` with respect to the ideal `I`.
