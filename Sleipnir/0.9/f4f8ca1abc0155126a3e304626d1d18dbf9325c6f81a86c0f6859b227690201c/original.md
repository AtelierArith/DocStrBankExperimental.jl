```
get_longterm_temps(rgi_id::String, params::Parameters)
```

Calculate the long-term average temperatures for a given glacier.

# Arguments

  * `rgi_id::String`: The RGI (Randolph Glacier Inventory) identifier for the glacier.
  * `params::Parameters`: A `Parameters` object containing simulation parameters, including paths to necessary data files.

# Returns

  * `longterm_temps`: A vector of long-term average temperatures for the glacier.

# Description

This function reads the gridded data and raw climate data for the specified glacier, applies a temperature gradient correction based on the glacier's topography, and then calculates the long-term average temperatures by grouping the temperature data by year.
