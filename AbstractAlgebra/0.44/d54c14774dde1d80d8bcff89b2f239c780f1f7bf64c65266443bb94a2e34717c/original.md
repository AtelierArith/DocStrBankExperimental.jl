```
evaluate(a::MPolyRingElem{T}, vals::Vector{U}) where {T <: RingElement, U <: NCRingElem}
```

Evaluate the polynomial expression at the supplied values, which may be any ring elements, commutative or non-commutative, but in the same ring. Evaluation always proceeds in the order of the variables as supplied when creating the polynomial ring to which $a$ belongs. The evaluation will succeed if a product of a coefficient of the polynomial by one of the values is defined.
