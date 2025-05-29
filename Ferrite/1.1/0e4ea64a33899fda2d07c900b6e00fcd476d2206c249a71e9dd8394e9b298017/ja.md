```
FacetIterator(gridordh::Union{Grid,AbstractDofHandler}, facetset::AbstractVecOrSet{FacetIndex})
```

`FacetIterator`を作成して、`facetset`内の面を便利に反復処理します。イテレータの要素は、適切に`reinit!`初期化された[`FacetCache`](@ref)です。詳細については[`FacetCache`](@ref)を参照してください。

`FacetIterator`をループすること、すなわち：

```julia
for fc in FacetIterator(grid, facetset)
    # ...
end
```

は、次の同等のスニペットの単なる便利さです：`julia fc = FacetCache(grid) for faceindex in facetset     reinit!(fc, faceindex)     # ... end`
