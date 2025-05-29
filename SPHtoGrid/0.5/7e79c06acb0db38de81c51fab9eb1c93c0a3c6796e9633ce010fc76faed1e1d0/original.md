```
surface_brightness_to_luminosity(map::Matrix{<:Real}, pixelSideLength::Real; unit_factor::Real=1.0)
```

Converts a map of surface brightness to luminosity per pixel. Uses `pixelSideLength` as the diameter of a pixel in `[kpc]`. If `unit_factor` is provided it is multiplied to every pixel to perform unit conversion.
