```
`mutable struct ProdOp{T}`
```

struct describing the result of a composition/product of operators.   Describing the composition using a dedicated type has the advantage   that the latter can be made copyable. This is particularly relevant for   multi-threaded code
