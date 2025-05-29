```
ustrip(x::Array{Q}) where {Q <: Quantity}
```

Strip units from an `Array` by reinterpreting to type `T`. The resulting `Array` is a not a copy, but rather a unit-stripped view into array `x`. Because the units are removed, information may be lost and this should be used with some care.

This function is provided primarily for compatibility purposes; you could pass the result to PyPlot, for example.

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
