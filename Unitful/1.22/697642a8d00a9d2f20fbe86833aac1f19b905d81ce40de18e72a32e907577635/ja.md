```
unit(x::Number)
```

普通の数値には単位がないことを示すために、[`NoUnits`](@ref)オブジェクトを返します。単位は空の文字列として表示されます。

例:

```jldoctest
julia> typeof(unit(1.0))
Unitful.FreeUnits{(), NoDims, nothing}

julia> typeof(unit(Float64))
Unitful.FreeUnits{(), NoDims, nothing}

julia> unit(1.0) == NoUnits
true
```
