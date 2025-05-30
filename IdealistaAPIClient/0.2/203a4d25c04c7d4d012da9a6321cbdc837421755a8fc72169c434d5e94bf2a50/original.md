```
valid_fields(;indent::Int=1)
```

Prints fieldnames of all SearchFields subtypes

Prints to stdout names and fieldnames of subtypes of SearchFields

# Keyword Arguments

  * indent: number of tabs of indentation

# Examples

```julia
julia>valid_fields()
Search
	country
	operation
	propertyType
	center
	distance
	locationId
	maxItems
	numPage
	maxPrice
	minPrice
	sinceDate
	order
	sort
	adIds
	hasMultimedia
Bedrooms
	housemates
	smokePolicy
	petsPolicy
	gayPartners
	newGender
Garages
	bankOffer
	automaticDoor
	motorcycleParking
	security
Homes
	minSize
	maxSize
	virtualTour
	flat
	penthouse
	duplex
	studio
	chalet
	countryHouse
	bedrooms
	bathrooms
	preservation
	newDevelopment
	furnished
	bankOffer
	garage
	terrace
	exterior
	elevator
	swimmingPool
	airConditioning
	storeRoom
	clotheslineSpace
	builtinWardrobes
	subTypology
Offices
	minSize
	maxSize
	layout
	buildingType
	garage
	hotWater
	heating
	elevator
	airConditioning
	security
	exterior
	bankOffer
Premises
	minSize
	maxSize
	virtualTour
	location
	corner
	airConditioning
	smokeVentilation
	heating
	transfer
	buildingTypes
	bankOffer

```
