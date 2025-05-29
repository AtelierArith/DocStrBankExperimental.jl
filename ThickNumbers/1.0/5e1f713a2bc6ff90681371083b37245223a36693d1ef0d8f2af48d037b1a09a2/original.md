```
loval(x::ThickNumber)
```

The value representing the lower limit of the span of `x`. `loval` must be implemented by any subtype of `ThickNumber`.

# Examples

```julia
julia> loval(Interval(1, 2))    # suppose Interval{T} <: ThickNumber{T}
1
```
