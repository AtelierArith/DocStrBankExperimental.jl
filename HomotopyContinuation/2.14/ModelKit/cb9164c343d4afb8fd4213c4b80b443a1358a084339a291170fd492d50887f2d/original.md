```
variables(prefix::Union{Symbol,String}, indices...)
```

Create an `Array` of variables with the given `prefix` and indices. The expression  `@var x[1:3, 1:2]` is equivalent to  `x = variables(:x, 1:3, 1:2)`.
