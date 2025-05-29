```
valuetype(::Type{<:ThickNumber})
```

Return the type of the numbers in the span, i.e., the `T` in `ThickNumber{T}`.

# Examples

```julia
julia> valuetype(Interval{Float64})
Float64
```
