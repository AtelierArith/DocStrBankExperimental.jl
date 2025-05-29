```
compare(a, b, order::Type{<:AbstractMonomialOrdering})
```

Returns a negative number if `a < b`, a positive number if `a > b` and zero if `a == b`. The comparison is done according to `order`.

**Warning** This is deprecated, use `cmp(order(), a, b)` instead.
