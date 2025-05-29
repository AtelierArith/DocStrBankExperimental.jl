```
batch_geocode(
    geocoder::Geocoder,
    input::Union{AbstractString, IO},
    output::Union{AbstractString, IO};
    workers::Int = 4,
    retries::Int = 5,
    timeout::Float64 = 60.0,
    input_columns::Union{Vector{Int}, Nothing} = nothing,
    add_columns::Vector{<:AbstractString} = ["formatted", "geometry.lat", "geometry.lng", "confidence", "components._type", "status_message"],
    on_error::Symbol = :log,
    ordered::Bool = false,
    progress::Bool = true,
    limit::Union{Int, Nothing} = nothing,
    optional_api_params::Dict{Symbol, Any} = Dict{Symbol, Any}(),
    rate_limit_semaphore::Union{Base.Semaphore, Nothing} = nothing,
    command::Union{Symbol, Nothing} = nothing
)
```

Process a batch of geocoding requests from a CSV file or IO stream.

This function efficiently processes large datasets by using multiple worker tasks to perform geocoding operations concurrently. It reads from the input CSV, geocodes each row, and writes the results to the output CSV.

# Arguments

  * `geocoder::Geocoder`: The geocoder instance to use for the requests
  * `input::Union{AbstractString, IO}`: The input CSV file path or IO stream
  * `output::Union{AbstractString, IO}`: The output CSV file path or IO stream

# Optional Parameters

  * `workers::Int = 4`: Number of concurrent worker tasks
  * `retries::Int = 5`: Number of retries for failed requests
  * `timeout::Float64 = 60.0`: Request timeout in seconds
  * `input_columns::Union{Vector{Int}, Nothing} = nothing`: Specific columns to use for geocoding (1-based indexing)

      * If `nothing`, all columns are used to form the query
      * If a single column is specified, it's used as the address for forward geocoding
      * If two columns are specified, they're used as latitude and longitude for reverse geocoding
  * `add_columns::Vector{<:AbstractString} = ["formatted", "geometry.lat", "geometry.lng", "confidence", "components._type", "status_message"]`: Fields from the geocoding result to add as output columns
  * `on_error::Symbol = :log`: How to handle errors during processing

      * `:log`: Log errors and continue processing (default)
      * `:skip`: Skip rows with errors
      * `:fail`: Stop processing on any error
  * `ordered::Bool = false`: Whether to preserve the input row order in the output
  * `progress::Bool = true`: Whether to display a progress bar
  * `limit::Union{Int, Nothing} = nothing`: Maximum number of rows to process
  * `optional_api_params::Dict{Symbol, Any} = Dict{Symbol, Any}()`: Additional parameters to pass to the API
  * `rate_limit_semaphore::Union{Base.Semaphore, Nothing} = nothing`: Optional semaphore for rate limiting
  * `command::Union{Symbol, Nothing} = nothing`: Force a specific geocoding command

      * `:forward`: Force forward geocoding
      * `:reverse`: Force reverse geocoding
      * `nothing`: Auto-detect based on input columns

# Returns

  * `nothing`: The function writes results to the output file/stream

# Throws

  * `BatchProcessingError`: If an error occurs during batch processing
  * `InvalidInputError`: If the input parameters are invalid

# Examples

```julia
# Basic usage with file paths
batch_geocode(
    geocoder,
    "input.csv",
    "output.csv"
)

# With custom options
batch_geocode(
    geocoder,
    "input.csv",
    "output.csv",
    workers=8,
    input_columns=[2],  # Use the second column for geocoding
    add_columns=["formatted", "geometry.lat", "geometry.lng", "components.country"],
    on_error=:skip,
    ordered=true,
    progress=true
)

# Reverse geocoding with coordinates in columns 1 and 2
batch_geocode(
    geocoder,
    "coordinates.csv",
    "addresses.csv",
    input_columns=[1, 2],  # Latitude and longitude columns
    command=:reverse
)
```
