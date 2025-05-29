```
allind(::Union{TT,Type{TT}}) where {TT<:AbstractTensorMap} -> Tuple{Int}
```

テンソルのすべてのインデックスを返します。すなわち、そのドメインとコドメインのインデックスです。

[`codomainind`](@ref) と [`domainind`](@ref) も参照してください。
