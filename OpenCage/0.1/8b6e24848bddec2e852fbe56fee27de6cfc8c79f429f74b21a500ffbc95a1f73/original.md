```
geocode_async(geocoder::Geocoder, query::AbstractString; kwargs...)::Task{Response}
```

Perform asynchronous forward geocoding to convert a place name or address to coordinates.

This function returns a `Task` that can be awaited or fetched to get the result.

# Arguments

  * `geocoder::Geocoder`: The geocoder instance to use for the request
  * `query::AbstractString`: The place name or address to geocode
  * `kwargs...`: Optional parameters to pass to the API (same as `geocode`)

# Returns

  * `Task{Response}`: A task that will resolve to the API response

# Throws

  * `InvalidInputError`: If the query is empty
  * Other exceptions may be thrown when the task is awaited/fetched

# Examples

```julia
geocoder = Geocoder("your-api-key")
task = geocode_async(geocoder, "Berlin, Germany")

# Do other work...

# Get the result when needed
response = fetch(task)
```
