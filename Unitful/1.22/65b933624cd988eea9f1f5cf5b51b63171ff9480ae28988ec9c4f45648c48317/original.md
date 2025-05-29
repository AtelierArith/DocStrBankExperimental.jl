```
reflevel(x::Level{L,S})
reflevel(::Type{Level{L,S}})
reflevel(::Type{Level{L,S,T}})
```

Returns the reference level, e.g.

```jldoctest
julia> reflevel(3u"dBm")
1 mW
```
