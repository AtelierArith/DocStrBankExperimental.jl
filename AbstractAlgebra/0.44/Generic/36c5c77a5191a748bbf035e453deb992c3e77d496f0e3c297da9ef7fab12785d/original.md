```
evaluate(a::U, vars::Vector{U}, vals::Vector{U}) where {T <: RingElement, U <: AbsMSeries{T}}
```

Evaluate the series expression by substituting in the supplied values in the array `vals` for the corresponding variables given by the array `vars`. The values must be in the same ring as $a$.
