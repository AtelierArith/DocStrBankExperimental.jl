```
OpenCage
```

A Julia SDK for the [OpenCage Geocoding API](https://opencagedata.com/api).

This package provides a comprehensive interface to the OpenCage Geocoding API, allowing for both forward geocoding (converting place names/addresses to coordinates) and reverse geocoding (converting coordinates to place names/addresses).

# Features

  * Forward geocoding (convert place names/addresses to coordinates)
  * Reverse geocoding (convert coordinates to place names/addresses)
  * Asynchronous API for both forward and reverse geocoding
  * Batch processing for large datasets with configurable concurrency
  * Comprehensive error handling
  * Rate limit detection and management
  * Support for all OpenCage API parameters

# Basic Usage

```julia
using OpenCage

# Create a geocoder instance
geocoder = Geocoder()  # Uses OPENCAGE_API_KEY environment variable
# Or: geocoder = Geocoder("your-api-key")

# Forward geocoding
response = geocode(geocoder, "Berlin, Germany")
if !isempty(response.results)
    result = response.results[1]
    println("Coordinates: $(result.geometry.lat), $(result.geometry.lng)")
end

# Reverse geocoding
response = reverse_geocode(geocoder, 52.5200, 13.4050)
if !isempty(response.results)
    result = response.results[1]
    println("Address: $(result.formatted)")
end
```

See the examples directory for more detailed usage examples.
