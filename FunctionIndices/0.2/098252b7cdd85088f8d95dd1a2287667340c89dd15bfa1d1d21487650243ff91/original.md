```
NotIndex{T} <: AbstractNotIndex{T}
```

The default implementation of [`not`](@ref). There are some optimization for `NotIndex(x)` comparing to `FI(!in(x))`. For large arrays, this implementation may be faster. but for small arrays this implementation may be slower. See [performance comparing](@ref performance) for more details.
