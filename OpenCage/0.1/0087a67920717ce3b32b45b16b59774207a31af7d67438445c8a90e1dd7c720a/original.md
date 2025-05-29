```
reverse_geocode_async(geocoder::Geocoder, latitude::Number, longitude::Number; kwargs...)::Task{Response}
```

Perform asynchronous reverse geocoding to convert coordinates to a place name or address.

This function returns a `Task` that can be awaited or fetched to get the result.

# Arguments

  * `geocoder::Geocoder`: The geocoder instance to use for the request
  * `latitude::Number`: The latitude coordinate
  * `longitude::Number`: The longitude coordinate
  * `kwargs...`: Optional parameters to pass to the API (same as `reverse_geocode`)

# Returns

  * `Task{Response}`: A task that will resolve to the API response

# Throws

  * `InvalidInputError`: If the coordinates are invalid
  * Other exceptions may be thrown when the task is awaited/fetched

# Examples

```julia
geocoder = Geocoder("your-api-key")
task = reverse_geocode_async(geocoder, 52.5200, 13.4050)

# Do other work...

# Get the result when needed
response = fetch(task)
```
