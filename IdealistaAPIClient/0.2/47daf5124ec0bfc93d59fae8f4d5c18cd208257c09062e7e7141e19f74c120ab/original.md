```
Garages <: PropertySearchFields
```

A struct that stores the garage specific search fields

Each field represents a valid garages search field for the Idealista Search API

# Constructors

```julia

Garages(bankOffer, automaticDoor, motorcycleParking, security)

Garages(; bankOffer::Union{Bool, Nothing}=nothing,
          automaticDoor::Union{Bool, Nothing}=nothing,
          motorcycleParking::Union{Bool, Nothing}=nothing,
          security::Union{Bool, Nothing}=nothing)
```

# Examples

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
