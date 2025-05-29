```
downscale_2D_climate(climate_step::Dict, glacier::Glacier2D) -> Climate2Dstep
```

Downscales climate data to a 2D grid based on the provided glacier information.

# Arguments

  * `climate_step::Dict`: A dictionary containing climate data for a specific time step. Expected keys are:

      * `"avg_temp"`: Average temperature.
      * `"temp"`: Temperature.
      * `"prcp"`: Precipitation.
      * `"gradient"`: Temperature gradient.
      * `"avg_gradient"`: Average temperature gradient.
      * `"ref_hgt"`: Reference height.
  * `glacier::Glacier2D`: A `Glacier2D` object containing glacier data. Expected fields are:

      * `S`: Surface elevation data.
      * `Coords`: A dictionary with keys `"lon"` and `"lat"` for longitude and latitude coordinates.

# Returns

  * `Climate2Dstep`: A `Climate2Dstep` object containing the downscaled climate data with fields:

      * `temp`: 2D array of temperature.
      * `PDD`: 2D array of positive degree days.
      * `snow`: 2D array of snow precipitation.
      * `rain`: 2D array of rain precipitation.
      * `gradient`: Temperature gradient.
      * `avg_gradient`: Average temperature gradient.
      * `x`: Longitude coordinates.
      * `y`: Latitude coordinates.
      * `ref_hgt`: Reference height.

# Description

This function creates dummy 2D arrays based on the glacier surface elevation data and applies the climate step data to these arrays. It then constructs a `Climate2Dstep` object with the downscaled climate data and applies temperature gradients to compute the snow/rain fraction for the selected period.
