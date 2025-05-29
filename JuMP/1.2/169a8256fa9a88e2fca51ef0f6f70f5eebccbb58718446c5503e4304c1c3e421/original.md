```
struct OptimizeNotCalled <: Exception end
```

A result attribute cannot be queried before [`optimize!`](@ref) is called.
