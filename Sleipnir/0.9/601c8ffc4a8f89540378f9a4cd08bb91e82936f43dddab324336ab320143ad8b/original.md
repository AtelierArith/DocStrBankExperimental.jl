```
initialize_glacier_climate!(glacier::AbstractGlacier, params::Parameters)
```

Initialize the climate data for a given glacier.

# Arguments

  * `glacier::AbstractGlacier`: The glacier object to initialize the climate data for.
  * `params::Parameters`: The parameters containing simulation settings and paths.

# Description

This function initializes the climate data for a glacier by:

1. Creating a dummy period based on the simulation time span and step.
2. Loading the raw climate data from a NetCDF file.
3. Calculating the cumulative climate data for the dummy period.
4. Downscaling the cumulative climate data to a 2D grid.
5. Retrieving long-term temperature data for the glacier.
6. Storing the climate data in the glacier object, including raw climate data, cumulative climate data, downscaled 2D climate data, long-term temperatures, average temperatures, and average gradients.
