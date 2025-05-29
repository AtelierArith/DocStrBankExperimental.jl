```
ustrip(x::Array{Q}) where {Q <: Quantity}
```

`Array` から単位を取り除くには、型 `T` に再解釈します。結果として得られる `Array` はコピーではなく、配列 `x` への単位を取り除いたビューです。単位が取り除かれるため、情報が失われる可能性があり、注意して使用する必要があります。

この関数は主に互換性の目的で提供されています。たとえば、結果を PyPlot に渡すことができます。

```jldoctest
julia> a = [1u"m", 2u"m"]
2-element Vector{Quantity{Int64, 𝐋, Unitful.FreeUnits{(m,), 𝐋, nothing}}}:
 1 m
 2 m

julia> b = ustrip(a)
2-element reinterpret(Int64, ::Vector{Quantity{Int64, 𝐋, Unitful.FreeUnits{(m,), 𝐋, nothing}}}):
 1
 2

julia> a[1] = 3u"m"; b
2-element reinterpret(Int64, ::Vector{Quantity{Int64, 𝐋, Unitful.FreeUnits{(m,), 𝐋, nothing}}}):
 3
 2
```
