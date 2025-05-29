```julia
initialize!(
    land_sea_mask::SpeedyWeather.EarthLandSeaMask,
    model::SpeedyWeather.PrimitiveEquation
) -> AbstractArray

```

Reads a high-resolution land-sea mask from file and interpolates (grid-cell average) onto the model grid for a fractional sea mask.
