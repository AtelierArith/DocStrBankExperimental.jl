```
Bedrooms <: PropertySearchFields
```

A struct that stores the bedrooms specific search fields

Each field represents a valid bedrooms search field for the Idealista Search API

# Constructors

```julia

Bedrooms(housemates,
         smokePolicy,
         petsPolicy,gayPartners,
         newGender)

Bedrooms(; housemates::Union{<:AbstractString, Nothing}=nothing,
           smokePolicy::Union{<:AbstractString, Nothing}=nothing,
           petsPolicy::Union{<:AbstractString, Nothing}=nothing,
           gayPartners::Union{Bool, Nothing}=nothing,
           newGender::Union{<:AbstractString, Nothing}=nothing)
```

# Examples

```jldoctest
julia> Bedrooms("2,4", "disallowed", "disallowed", true, "male")
Bedrooms:
	housemates => 2,4
	smokePolicy => disallowed
	petsPolicy => disallowed
	gayPartners => true
	newGender => male

julia> Bedrooms(housemates="2,4", smokePolicy="disallowed", petsPolicy="disallowed", gayPartners=true, newGender="male")
Bedrooms:
	housemates => 2,4
	smokePolicy => disallowed
	petsPolicy => disallowed
	gayPartners => true
	newGender => male
```
