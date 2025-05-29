```
VIDAMovie(mov::IntensityMap{T,3})
```

Create an VIDAMovie class for easy interpolation between frames.

# Arguments

  * `mov`: An IntensityMap with axes (:X, :Y, :T) that represent the frames of a movie.  Note that the time dimension does not have to be equi-spaced.

# Returns

An `VIDAMovie` object that behaves like `IntensityMap` but lets you interpolate between frames with [`get_image(vida_movie, time)`](@ref).
