```
Premises <: PropertySearchFields
```

A struct that stores the premises specific search fields

Each field represents a valid premises search field for the Idealista Search API

# Constructors

```julia

Premises(minSize,
         maxSize,
         virtualTour,
         location,
         corner,
         airConditioning,
         smokeVentilation,
         heating,
         transfer,
         buildingTypes,
         bankOffer)

Premises(; minSize::Union{<:Number, Nothing}=nothing,
           maxSize::Union{<:Number, Nothing}=nothing,
           virtualTour::Union{Bool, Nothing}=nothing,
           location::Union{<:AbstractString, Nothing}=nothing,
           corner::Union{Bool, Nothing}=nothing,
           airConditioning::Union{Bool, Nothing}=nothing,
           smokeVentilation::Union{Bool, Nothing}=nothing,
           heating::Union{Bool, Nothing}=nothing,
           transfer::Union{Bool, Nothing}=nothing,
           buildingTypes::Union{<:AbstractString, Nothing}=nothing,
           bankOffer::Union{Bool, Nothing}=nothing)
```

# Examples

```jldoctest
julia> Premises(70, 120, false, "shoppingcenter", false, true, false, true, false, "industrialBuilding", false)
[ Info: bankOffer only applies in Spain
Premises:
	minSize => 70
	maxSize => 120
	virtualTour => false
	location => shoppingcenter
	corner => false
	airConditioning => true
	smokeVentilation => false
	heating => true
	transfer => false
	buildingTypes => industrialBuilding
	bankOffer => false

julia> Premises(minSize=70, maxSize=120, transfer=false, location="shoppingcenter")
Premises:
	minSize => 70
	maxSize => 120
	virtualTour => nothing
	location => shoppingcenter
	corner => nothing
	airConditioning => nothing
	smokeVentilation => nothing
	heating => nothing
	transfer => false
	buildingTypes => nothing
	bankOffer => nothing
```
