```
unit(x::Quantity{T,D,U}) where {T,D,U}
unit(x::Type{Quantity{T,D,U}}) where {T,D,U}
```

`Quantity`または`Quantity`型に関連付けられた単位を返します。

例:

```jldoctest
julia> unit(1.0u"m") == u"m"
true

julia> unit(typeof(1.0u"m")) == u"m"
true
```
