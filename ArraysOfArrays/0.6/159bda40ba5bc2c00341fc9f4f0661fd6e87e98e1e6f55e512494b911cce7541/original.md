```
deepmap(f::Base.Callable, x::Any)
deepmap(f::Base.Callable, A::AbstractArray{<:AbstractArray{<:...}})
```

Applies `map` at the deepest possible layer of nested arrays. If `A` is not a nested array, `deepmap` behaves identical to `Base.map`.
