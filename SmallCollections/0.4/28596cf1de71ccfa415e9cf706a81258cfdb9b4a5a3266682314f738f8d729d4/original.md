```
sum_fast(s::AbstractSmallSet{N,T}) where {N,T}
```

Return the `@fastmath` sum of the elements of `s`. Unlike for `sum`, the return value always is of the element type of `s`, even for small bit integers.

See also `Base.sum`, `Base.@fastmath`.
