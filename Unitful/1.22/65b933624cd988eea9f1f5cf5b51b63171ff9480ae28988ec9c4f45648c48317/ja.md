```
reflevel(x::Level{L,S})
reflevel(::Type{Level{L,S}})
reflevel(::Type{Level{L,S,T}})
```

参照レベルを返します。例えば、

```jldoctest
julia> reflevel(3u"dBm")
1 mW
```
