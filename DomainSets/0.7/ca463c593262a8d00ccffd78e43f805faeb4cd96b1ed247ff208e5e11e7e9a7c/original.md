```
equaldomain(domain)
```

Return a canonical domain that is equal, but simpler. For example, a 1-dimensional ball is an interval. This function is equivalent to `canonicaldomain(Equal(), d)`.

A domain and its `equaldomain` are always equal domains according to `isequaldomain`.

See also: [`canonicaldomain`](@ref).
