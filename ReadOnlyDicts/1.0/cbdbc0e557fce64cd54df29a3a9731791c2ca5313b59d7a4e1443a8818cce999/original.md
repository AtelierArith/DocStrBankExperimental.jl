```julia
struct ReadOnlyDict{K, V, D<:AbstractDict{K, V}} <: AbstractDict{K, V}
```

Wraps an `AbstractDict` and only implements non-mutating functions of the interface. The wrapped `AbstractDict` can be obtained using `Base.parent`. The standard dictionary constructors use `Base.Dict` as the inner collection.
