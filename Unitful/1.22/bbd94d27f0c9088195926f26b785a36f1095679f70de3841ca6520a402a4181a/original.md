```
unit(x::Quantity{T,D,U}) where {T,D,U}
unit(x::Type{Quantity{T,D,U}}) where {T,D,U}
```

Returns the units associated with a `Quantity` or `Quantity` type.

Examples:

```jldoctest
julia> unit(1.0u"m") == u"m"
true

julia> unit(typeof(1.0u"m")) == u"m"
true
```
