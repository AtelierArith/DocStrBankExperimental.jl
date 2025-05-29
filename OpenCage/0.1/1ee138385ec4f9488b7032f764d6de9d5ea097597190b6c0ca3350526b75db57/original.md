```
reverse_geocode(geocoder::Geocoder, latitude::Number, longitude::Number; kwargs...)::Response
```

Perform reverse geocoding to convert coordinates to a place name or address.

# Arguments

  * `geocoder::Geocoder`: The geocoder instance to use for the request
  * `latitude::Number`: The latitude coordinate
  * `longitude::Number`: The longitude coordinate
  * `kwargs...`: Optional parameters to pass to the API

# Optional Parameters

  * `language::AbstractString`: Preferred language for results
  * `no_annotations::Bool`: Exclude annotations from results
  * `no_record::Bool`: Don't store the query in the OpenCage database
  * And many more (see OpenCage API documentation)

# Returns

  * `Response`: The API response containing geocoding results

# Throws

  * `InvalidInputError`: If the coordinates are invalid
  * `NotAuthorizedError`: If the API key is invalid
  * `RateLimitExceededError`: If the rate limit has been exceeded
  * `NetworkError`: If a network error occurs
  * Other `OpenCageError` subtypes for various error conditions

# Examples

```julia
geocoder = Geocoder("your-api-key")
response = reverse_geocode(geocoder, 52.5200, 13.4050)

# With optional parameters
response = reverse_geocode(geocoder, 51.5074, -0.1278,
    language="fr",
    no_annotations=true
)
```
