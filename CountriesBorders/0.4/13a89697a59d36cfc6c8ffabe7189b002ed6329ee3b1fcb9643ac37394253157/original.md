```
extract_plot_coords([T::Type{<:AbstractFloat} = Float32], item)
```

Returns a NamedTuple with two vectors `lat` and `lon` containing the corresponding coordinates of all the points contained within the provided `item`.

This is mostly intended to simplify creation of the `lat` and `lon` keyword arguments to provide to the `scattergeo` function from `PlotlyBase`. By default points are converted to Float32 and NaN values are inserted between each `Ring` to allow plotting multiple polyareas within a single trace.
