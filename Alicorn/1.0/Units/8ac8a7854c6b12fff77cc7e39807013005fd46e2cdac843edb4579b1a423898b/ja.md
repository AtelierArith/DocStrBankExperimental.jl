```
listBaseUnits(unitCatalogue::UnitCatalogue)
```

`unitCatalogue`に格納されている[`BaseUnit`](@ref)オブジェクトをその名前でインデックス付けした辞書を返します。

# 例

```jldoctest
julia> ucat = UnitCatalogue() ;

julia> baseUnits = listBaseUnits(ucat) ;

julia> baseUnits["siemens"]
BaseUnit siemens (1 S = 1 kg^-1 m^-2 s^3 A^2)
```
