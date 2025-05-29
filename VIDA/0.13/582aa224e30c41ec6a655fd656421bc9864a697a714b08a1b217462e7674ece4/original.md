```julia
get_image(mov, t; keeptime)

```

Gets the frame of the movie object `mov` at the time t. This returns an `IntensityMap` object at the requested time. The returned object is found by linear interpolation.
