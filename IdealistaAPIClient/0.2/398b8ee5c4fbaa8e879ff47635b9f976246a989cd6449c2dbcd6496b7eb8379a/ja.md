```
Homes <: PropertySearchFields
```

特定の住宅検索フィールドを格納する構造体

各フィールドは、Idealista Search APIの有効な住宅検索フィールドを表します。

# コンストラクタ

```julia

Homes(minSize,
      maxSize,
      virtualTour,
      flat,
      penthouse,
      duplex,
      studio,
      chalet,
      countryHouse,
      bedrooms,
      bathrooms,
      preservation,
      newDevelopment,
      furnished,
      bankOffer,
      garage,
      terrace,
      exterior,
      elevator,
      swimmingPool,
      airConditioning,
      storeRoom,
      clotheslineSpace,
      builtinWardrobes,
      subTypology)

struct Homes(; minSize::Union{<:Number, Nothing}=nothing,
               maxSize::Union{<:Number, Nothing}=nothing,
               virtualTour::Union{Bool, Nothing}=nothing,
               flat::Union{Bool, Nothing}=nothing,
               penthouse::Union{Bool, Nothing}=nothing,
               duplex::Union{Bool, Nothing}=nothing,
               studio::Union{Bool, Nothing}=nothing,
               chalet::Union{Bool, Nothing}=nothing,
               countryHouse::Union{Bool, Nothing}=nothing,
               bedrooms::Union{<:AbstractString, Nothing}=nothing,
               bathrooms::Union{<:AbstractString, Nothing}=nothing,
               preservation::Union{<:AbstractString, Nothing}=nothing,
               newDevelopment::Union{Bool, Nothing}=nothing,
               furnished::Union{<:AbstractString, Nothing}=nothing,
               bankOffer::Union{Bool, Nothing}=nothing,
               garage::Union{Bool, Nothing}=nothing,
               terrace::Union{Bool, Nothing}=nothing,
               exterior::Union{Bool, Nothing}=nothing,
               elevator::Union{Bool, Nothing}=nothing,
               swimmingPool::Union{Bool, Nothing}=nothing,
               airConditioning::Union{Bool, Nothing}=nothing,
               storeRoom::Union{Bool, Nothing}=nothing,
               clotheslineSpace::Union{Bool, Nothing}=nothing,
               builtinWardrobes::Union{Bool, Nothing}=nothing,
               subTypology::Union{<:AbstractString, Nothing}=nothing)

```

# 例

```jldoctest
julia> Homes(65, 130, false, true, true, true, true, true, true, "1,2,3,4", "1,2", "good", true, "furnished", false, true, true, false, false, false, false, false, false, true, "independantHouse")
[ Info: bankOffer only applies in Spain
Homes:
	minSize => 65
	maxSize => 130
	virtualTour => false
	flat => true
	penthouse => true
	duplex => true
	studio => true
	chalet => true
	countryHouse => true
	bedrooms => 1,2,3,4
	bathrooms => 1,2
	preservation => good
	newDevelopment => true
	furnished => furnished
	bankOffer => false
	garage => true
	terrace => true
	exterior => false
	elevator => false
	swimmingPool => false
	airConditioning => false
	storeRoom => false
	clotheslineSpace => false
	builtinWardrobes => true
	subTypology => independantHouse


julia> Homes(minSize=70, swimmingPool=false, preservation="renew", subTypology="terracedHouse")
Homes:
	minSize => 70
	maxSize => nothing
	virtualTour => nothing
	flat => nothing
	penthouse => nothing
	duplex => nothing
	studio => nothing
	chalet => nothing
	countryHouse => nothing
	bedrooms => nothing
	bathrooms => nothing
	preservation => renew
	newDevelopment => nothing
	furnished => nothing
	bankOffer => nothing
	garage => nothing
	terrace => nothing
	exterior => nothing
	elevator => nothing
	swimmingPool => false
	airConditioning => nothing
	storeRoom => nothing
	clotheslineSpace => nothing
	builtinWardrobes => nothing
	subTypology => terracedHouse
```
