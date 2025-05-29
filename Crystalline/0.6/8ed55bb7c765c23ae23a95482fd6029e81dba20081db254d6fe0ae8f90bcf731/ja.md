```
irreps(n::AbstractSymmetryVector{D}) -> AbstractVector{<:Collection{<:AbstractIrrep{D}}}
```

`n`によって参照されるirrepsを返します。

返される値は、同じ`Collection`に属する特定の**k**-多様体に関連する異なるグループのirrepsを持つ`Collection{<:AbstractIrrep}`の`AbstractVector`です。

[`multiplicities(::AbstractSymmetryVector)`](@ref)も参照してください。
