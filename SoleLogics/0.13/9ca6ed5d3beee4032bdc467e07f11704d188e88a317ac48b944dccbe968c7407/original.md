```
iscrisp(a::AbstractAlgebra) = iscrisp(typeof(a))
```

An algebra is crisp (or *boolean*) when its domain only has two values, namely, the top and the bottom. The antonym of crisp is *fuzzy*.

See also [`AbstractAlgebra`](@ref).
