```
initialize_glaciers(
    rgi_ids::Vector{String},
    params::Parameters;
    velocityDatacubes::Union{Dict{String, String}, Dict{String, RasterStack}}=Dict(),
)
```

Initialize glaciers based on provided RGI IDs and parameters.

# Arguments

  * `rgi_ids::Vector{String}`: A vector of RGI IDs representing the glaciers to be initialized.
  * `params::Parameters`: A `Parameters` object containing simulation parameters.
  * `test::Bool`: An optional boolean flag indicating whether to run in test mode. Default is `false`.
  * `velocityDatacubes::Union{Dict{String, String}, Dict{String, RasterStack}}`: A dictionary that provides for each RGI ID either the path to the datacube or the `RasterStack` with velocity data.

# Returns

  * `glaciers::Vector{Glacier2D}`: A vector of initialized `Glacier2D` objects.

# Description

This function performs the following steps:

1. Generates a file for missing glaciers if it does not already exist.
2. Filters out missing glaciers from the provided RGI IDs.
3. Generates raw climate data for the glaciers if necessary.
4. Initializes the glaciers using the provided RGI IDs and parameters.
5. If `use_glathida_data` is enabled in the simulation parameters, assigns GlaThiDa data to the glaciers.

# Errors

  * Throws an error if none of the provided RGI IDs have GlaThiDa data.

# Warnings

  * Issues a warning if not all glaciers have GlaThiDa data available.

# Example

```julia
# We declare a list of glaciers to be initialized with their RGI IDs
rgi_ids = ["RGI60-11.03638", "RGI60-11.01450", "RGI60-11.02346", "RGI60-08.00203"]
# We initialize those glaciers based on the RGI IDs and the parameters we previously specified
glaciers = initialize_glaciers(rgi_ids, params)
```
