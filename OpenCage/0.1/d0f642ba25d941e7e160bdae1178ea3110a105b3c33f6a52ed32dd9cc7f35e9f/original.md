```
geocode(geocoder::Geocoder, query::AbstractString; kwargs...)::Response
```

Perform forward geocoding to convert a place name or address to coordinates.

# Arguments

  * `geocoder::Geocoder`: The geocoder instance to use for the request
  * `query::AbstractString`: The place name or address to geocode
  * `kwargs...`: Optional parameters to pass to the API

# Optional Parameters

  * `language::AbstractString`: Preferred language for results
  * `countrycode::Union{AbstractString, Vector{<:AbstractString}}`: Limit results to specific countries
  * `bounds::NTuple{4, Number}`: Restrict results to within a bounding box (min*lng, min*lat, max*lng, max*lat)
  * `proximity::NTuple{2, Number}`: Bias results towards a specific location (lat, lng)
  * `limit::Integer`: Maximum number of results to return
  * `no_annotations::Bool`: Exclude annotations from results
  * `no_record::Bool`: Don't store the query in the OpenCage database
  * And many more (see OpenCage API documentation)

# Returns

  * `Response`: The API response containing geocoding results

# Throws

  * `InvalidInputError`: If the query is empty
  * `NotAuthorizedError`: If the API key is invalid
  * `RateLimitExceededError`: If the rate limit has been exceeded
  * `NetworkError`: If a network error occurs
  * Other `OpenCageError` subtypes for various error conditions

# Examples

```julia
geocoder = Geocoder("your-api-key")
response = geocode(geocoder, "Berlin, Germany")

# With optional parameters
response = geocode(geocoder, "London",
    language="fr",
    countrycode="gb",
    limit=5,
    no_annotations=true
)
```
