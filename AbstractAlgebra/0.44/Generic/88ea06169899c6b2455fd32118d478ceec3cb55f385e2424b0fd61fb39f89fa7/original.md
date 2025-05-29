```
evaluate(a::U, vals::Vector{U}) where {T <: RingElement, U <: AbsMSeries{T}}
```

Evaluate the series expression by substituting in the supplied values in the array `vals` for the variables the series ring to which $a$ belongs. The values must be in the same ring as $a$.
