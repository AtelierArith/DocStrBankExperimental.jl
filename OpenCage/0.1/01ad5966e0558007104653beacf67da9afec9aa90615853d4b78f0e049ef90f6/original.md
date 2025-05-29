```
Geocoder
```

A client for the OpenCage Geocoding API.

The `Geocoder` struct holds the API key and configuration options for making requests to the OpenCage Geocoding API.

# Fields

  * `api_key::String`: The OpenCage API key
  * `api_base_url::String`: The base URL for the OpenCage API
  * `user_agent::String`: The User-Agent string to use in requests
  * `timeout::Float64`: Request timeout in seconds
  * `retries::Int`: Number of retries for failed requests
  * `retry_options::Dict{Symbol, Any}`: Options for retry behavior
  * `extra_http_options::Dict{Symbol, Any}`: Additional HTTP options

# Constructors

```julia
Geocoder(
    api_key::AbstractString;
    api_base_url::AbstractString = "https://api.opencagedata.com/geocode/v1/json",
    user_agent_comment::Union{AbstractString, Nothing} = nothing,
    timeout::Real = 60.0,
    retries::Integer = 5,
    retry_options::Dict = Dict{Symbol, Any}(:max_delay => 60.0, :factor => 1.0, :jitter => 0.1),
    extra_http_options::Dict = Dict{Symbol, Any}()
)
```

Creates a new `Geocoder` with the specified API key and options.

```julia
Geocoder(; kwargs...)
```

Creates a new `Geocoder` using the API key from the `OPENCAGE_API_KEY` environment variable.

# Examples

```julia
# Using an explicit API key
geocoder = Geocoder("your-api-key")

# Using the environment variable
ENV["OPENCAGE_API_KEY"] = "your-api-key"
geocoder = Geocoder()

# With custom options
geocoder = Geocoder(
    "your-api-key",
    timeout=30.0,
    retries=3,
    user_agent_comment="MyApp/1.0"
)
```
