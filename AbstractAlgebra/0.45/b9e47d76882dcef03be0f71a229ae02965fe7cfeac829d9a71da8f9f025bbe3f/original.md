```
evaluate(a::MPolyRingElem{T}, vals::Vector{U}) where {T <: RingElement, U <: RingElement}
```

Evaluate the polynomial expression by substituting in the array of values for each of the variables. The evaluation will succeed if multiplication is defined between elements of the coefficient ring of $a$ and elements of the supplied vector.
