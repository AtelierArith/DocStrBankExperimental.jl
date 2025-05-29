```
evaluate(a::S, vars::Vector{S}, vals::Vector{U}) where {S <: MPolyRingElem{T}, U <: RingElement} where T <: RingElement
```

Evaluate the polynomial expression by substituting in the supplied values in the array `vals` for the corresponding variables (supplied as polynomials) given by the array `vars`. The evaluation will succeed if multiplication is defined between elements of the coefficient ring of $a$ and elements of `vals`.
