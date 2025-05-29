```
@kwcall f(b,a,c=0)
```

Declares that any call `f(::NamedTuple{N})` with `sort(N) == (:a,:b,:c)` should be dispatched to the method already defined on `f(::NamedTuple{(:b,:a,:c)})`

Note that in the example `@kwcall f(b,a,c=0)`, the macro checks for existence of `f(::NamedTuple)` and `f(; kwargs...)` methods, and only creates new ones if these don't already exist.
