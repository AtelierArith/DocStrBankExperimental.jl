```
get_longterm_temps(rgi_id::String, params::Parameters, climate::RasterStack) -> Array{Float64}
```

Calculate the long-term average temperatures for a given glacier.

# Arguments

  * `rgi_id::String`: The RGI (Randolph Glacier Inventory) identifier for the glacier.
  * `params::Parameters`: A struct containing simulation parameters, including paths to RGI data.
  * `climate::RasterStack`: A `RasterStack` object containing climate data.

# Returns

  * `Array{Float64}`: An array of long-term average temperatures.

# Description

This function retrieves the gridded data for the specified glacier using its RGI identifier. It then applies a temperature gradient to the climate data based on the glacier's topography. Finally, it calculates the long-term average temperatures by grouping the temperature data by year and computing the mean for each group.
