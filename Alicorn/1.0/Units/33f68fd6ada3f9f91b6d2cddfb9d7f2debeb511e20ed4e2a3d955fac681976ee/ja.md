```
listUnitPrefixes(unitCatalogue::UnitCatalogue)
```

`unitCatalogue`に格納されている[`UnitPrefix`](@ref)オブジェクトをその名前でインデックス付けした辞書を返します。

# 例

```jldoctest
julia> ucat = UnitCatalogue() ;

julia> prefixes = listUnitPrefixes(ucat) ;

julia> prefixes["micro"]
UnitPrefix micro (μ) of value 1e-6
```
