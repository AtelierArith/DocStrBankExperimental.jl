```
createT(a::Taylor0, cache::Taylor0)
```

puts the coefficients of `a` into cache and returns cache.

```jldoctest
using QuantizedSystemSolver
a = Taylor0([1.0, 1.0])
cache = Taylor0([0.0, 0.0])
createT(a, cache)
cache[0]

# output

1.0
```
