```
hival(x::ThickNumber)
```

The value representing the upper limit of the span of `x`. `hival` must be implemented by any subtype of `ThickNumber`.

# Examples

```julia
julia> hival(Interval(1, 2))    # suppose Interval{T} <: ThickNumber{T}
2
```
