```
downscale_2D_climate!(glacier::Glacier2D)
```

Update the 2D climate structure for a given glacier by downscaling climate data.

# Arguments

  * `glacier::Glacier2D`: The glacier object containing the climate data to be downscaled.

# Description

This function updates the 2D climate structure of the given glacier by:

1. Updating the temperature, PDD (Positive Degree Days), snow, and rain fields in the 2D climate step with the corresponding values from the climate step.
2. Updating the gradients and average gradients in the 2D climate step.
3. Applying temperature gradients and computing the snow/rain fraction for the selected period by reprojecting the current `S` with the `RasterStack` structure.

# Notes

  * The function modifies the `glacier` object in place.
