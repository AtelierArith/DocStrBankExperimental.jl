```
Garages <: PropertySearchFields
```

ガレージ特有の検索フィールドを格納する構造体

各フィールドは、Idealista Search API の有効なガレージ検索フィールドを表します。

# コンストラクタ

```julia

Garages(bankOffer, automaticDoor, motorcycleParking, security)

Garages(; bankOffer::Union{Bool, Nothing}=nothing,
          automaticDoor::Union{Bool, Nothing}=nothing,
          motorcycleParking::Union{Bool, Nothing}=nothing,
          security::Union{Bool, Nothing}=nothing)
```

# 例

```jldoctest
julia> Garages(nothing, true, true, false)
Garages:
	bankOffer => nothing
	automaticDoor => true
	motorcycleParking => true
	security => false

julia> Garages(automaticDoor=true, security=true)
Garages:
	bankOffer => nothing
	automaticDoor => true
	motorcycleParking => nothing
	security => true
```
