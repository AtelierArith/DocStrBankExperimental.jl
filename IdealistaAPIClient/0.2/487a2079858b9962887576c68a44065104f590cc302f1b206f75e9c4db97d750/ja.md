```
Offices <: PropertySearchFields
```

オフィス特有の検索フィールドを格納する構造体

各フィールドは、Idealista Search APIの有効なオフィス検索フィールドを表します。

# コンストラクタ

```julia

Offices(minSize,
        maxSize,
        layout,
        buildingType,
        garage,
        hotWater,
        heating,
        elevator,
        airConditioning,
        security,
        exterior,
        bankOffer)

Offices(; minSize::Union{<:Number, Nothing}=nothing,
          maxSize::Union{<:Number, Nothing}=nothing,
          layout::Union{<:AbstractString, Nothing}=nothing,
          buildingType::Union{<:AbstractString, Nothing}=nothing,
          garage::Union{Bool, Nothing}=nothing,
          hotWater::Union{Bool, Nothing}=nothing,
          heating::Union{Bool, Nothing}=nothing,
          elevator::Union{Bool, Nothing}=nothing,
          airConditioning::Union{Bool, Nothing}=nothing,
          security::Union{Bool, Nothing}=nothing,
          exterior::Union{Bool, Nothing}=nothing,
          bankOffer::Union{Bool, Nothing}=nothing)
```

# 例

```jldoctest
julia> Offices(100, 400, "withWalls", "exclusive", false, true, true, true, true, false, false, false)
[ Info: bankOffer only applies in Spain
Offices:
	minSize => 100
	maxSize => 400
	layout => withWalls
	buildingType => exclusive
	garage => false
	hotWater => true
	heating => true
	elevator => true
	airConditioning => true
	security => false
	exterior => false
	bankOffer => false


julia> Offices(minSize=100, maxSize=400, layout="withWalls", buildingType="exclusive")
Offices:
	minSize => 100
	maxSize => 400
	layout => withWalls
	buildingType => exclusive
	garage => nothing
	hotWater => nothing
	heating => nothing
	elevator => nothing
	airConditioning => nothing
	security => nothing
	exterior => nothing
	bankOffer => nothing
```
