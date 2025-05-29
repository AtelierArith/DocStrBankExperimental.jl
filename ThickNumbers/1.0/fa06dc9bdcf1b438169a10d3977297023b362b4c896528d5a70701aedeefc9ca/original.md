```
emptyset(::Type{TN}) where TN<:ThickNumber
emptyset(x::ThickNumber)
```

Construct an "empty set" of type `TN`.

# Default implementation

The default implementation creates an empty set by making the `loval` be bigger than the `hival`. Specifically, the default implementation is

```
emptyset(::Type{TN}) where TN<:ThickNumber{T} where T = lohi(TN, typemax(T), typemin(T))
```

# Examples

```julia
julia> emptyset(Interval{Float64})
Interval{Float64}(Inf, -Inf)
```
