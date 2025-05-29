```
innermap(f::Base.Callable, A::AbstractArray{<:AbstractArray})
```

Nested `map` at depth 2. Equivalent to `map(X -> map(f, X) A)`.
