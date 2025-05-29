```
evaluate(a::MPolyRingElem{T}, vars::Vector{Int}, vals::Vector{U}) where {T <: RingElement, U <: RingElement}
```

Evaluate the polynomial expression by substituting in the supplied values in the array `vals` for the corresponding variables with indices given by the array `vars`. The evaluation will succeed if multiplication is defined between elements of the coefficient ring of $a$ and elements of `vals`.
