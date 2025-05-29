```
sum_fast(v::AbstractFixedVector)
```

Return the `@fastmath` sum of the elements of `v`. Unlike for `sum`, the return value always is of the element type of `v`, even for small bit integers.

See also `Base.sum`, `Base.@fastmath`.
