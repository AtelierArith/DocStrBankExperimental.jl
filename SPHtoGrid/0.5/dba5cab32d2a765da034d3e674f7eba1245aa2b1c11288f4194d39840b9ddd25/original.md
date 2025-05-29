```
surface_brightness_to_luminosity(map::Matrix{<:Real}, par::mappingParameters; unit_factor::Real=1.0)
```

Converts a map of surface brightness to luminosity per pixel. If `unit_factor` is provided it is multiplied to every pixel to perform unit conversion.
