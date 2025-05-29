```
M = of_eltype(T, A)
M = of_eltype(val::T, A)
```

creates a view of `A` that lazily-converts the element type to `T`.
