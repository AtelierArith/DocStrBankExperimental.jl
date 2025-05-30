```
Search <: SearchFields
```

A struct that stores the basic (non-property-type specific) search fields of the Idealista Search API

Each field represents a valid base search field for the Idealista Search API. The country, operation, propertyType and center + distance or center + locationId are mandatory

# Constructors

```julia

Search(country,
       operation,
       propertyType,
       center,
       maxItems,
       numPage,
       maxPrice,
       minPrice,
       sinceDate,
       orderg,
       sort,
       adIds,
       hasMultimedia,
       distance,
       locationId,
       locale)

Search(; country::String,
         operation::String,
         propertyType::String,
         center::String,
         maxItems::Union{<:Int, Nothing}=nothing,
         numPage::Union{<:Int, Nothing}=nothing,
         maxPrice::Union{<:Number, Nothing}=nothing,
         minPrice::Union{<:Number, Nothing}=nothing,
         sinceDate::Union{<:AbstractString, Nothing}=nothing,
         order::Union{<:AbstractString, Nothing}=nothing,
         sort::Union{<:AbstractString, Nothing}=nothing,
         adIds::Union{<:Int, Nothing}=nothing,
         hasMultimedia::Union{Bool, Nothing}=nothing,
         distance::Union{<:Int, Nothing}=nothing,
         locationId::Union{<:AbstractString, Nothing}=nothing,
         locale::String)
```

# Examples

```jldoctest
julia> Search("es", "sale", "homes", "42.0,-3.7",  nothing, nothing, nothing, nothing, nothing, nothing, nothing, nothing, nothing, 15000,  nothing, "ca")
Search:
	country => es
	operation => sale
	propertyType => homes
	center => 42.0,-3.7
	maxItems => nothing
	numPage => nothing
	maxPrice => nothing
	minPrice => nothing
	sinceDate => nothing
	order => nothing
	sort => nothing
	adIds => nothing
	hasMultimedia => nothing
	distance => 15000
	locationId => nothing
	locale => ca

julia> Search(country="it", operation="sale", propertyType="homes", center="42.0,-3.7", locale="es", distance=15000)
Search:
	country => it
	operation => sale
	propertyType => homes
	center => 42.0,-3.7
	maxItems => nothing
	numPage => nothing
	maxPrice => nothing
	minPrice => nothing
	sinceDate => nothing
	order => nothing
	sort => nothing
	adIds => nothing
	hasMultimedia => nothing
	distance => 15000
	locationId => nothing
	locale => es

julia> Search("it", "sale", "homes", "42.0,-3.7", locale="es", distance=15000)
Search:
	country => it
	operation => sale
	propertyType => homes
	center => 42.0,-3.7
	maxItems => nothing
	numPage => nothing
	maxPrice => nothing
	minPrice => nothing
	sinceDate => nothing
	order => nothing
	sort => nothing
	adIds => nothing
	hasMultimedia => nothing
	distance => 15000
	locationId => nothing
	locale => es
```
