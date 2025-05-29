```
dimensionOf(quantity::AbstractQuantity)
```

物理量の次元を[`AbstractQuantity`](@ref)型で返します。

# 例

1ヘンリーは$1\,\mathrm{H} = 1\,\mathrm{kg}^{1}\,\mathrm{m}^{2}\,\mathrm{s}^{-2}\,\mathrm{A}^{-2}$として定義され、したがって次元は$\mathrm{M}^{1}\,\mathrm{L}^{2}\,\mathrm{T}^{-2}\,\mathrm{I}^{-2}$です：

```jldoctest
julia> ucat = UnitCatalogue() ;

julia> oneHenry = 1 * ucat.henry
1 H
julia> dimensionOf(oneHenry)
Dimension M^1 L^2 T^-2 I^-2
```
