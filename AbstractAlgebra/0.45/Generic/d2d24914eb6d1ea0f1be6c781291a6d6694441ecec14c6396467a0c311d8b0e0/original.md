```
evaluate(a::U, vars::Vector{Int}, vals::Vector{U}) where {T <: RingElement, U <: AbsMSeries{T}}
```

Evaluate the series expression by substituting in the supplied values in the array `vals` for the corresponding variables with indices given by the array `vars`. The values must be in the same ring as $a$.
