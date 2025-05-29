```
θ₀
```

弧の長さが半径と等しい平面円弧の中心角に等しい量。正確に1ラジアン、または約57.2958°の値を持つ。いくつかの提案されたSI拡張システムにおける角度次元の定義定数として使用される。

次元: 𝐀。

参照: [`DimensionfulAngles.radᵃ`](@ref)。

# 例

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles

julia> θ₀
1//1 rad

julia> θ₀ |> ua"°"
57.29577951308232°

julia> 2.1ua"rad" / θ₀
2.1
```
