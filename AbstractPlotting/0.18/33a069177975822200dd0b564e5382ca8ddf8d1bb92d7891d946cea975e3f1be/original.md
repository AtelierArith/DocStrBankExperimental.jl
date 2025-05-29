```
arc(origin, radius, start_angle, stop_angle; kwargs...)
```

This function plots a circular arc, centered at `origin` with radius `radius`, from `start_angle` to `stop_angle`. `origin` must be a coordinate in 2 dimensions (i.e., a `Point2`); the rest of the arguments must be `<: Number`.

Examples:

`arc(Point2f0(0), 1, 0.0, π)` `arc(Point2f0(1, 2), 0.3. π, -π)`

## Attributes

Available attributes and their defaults for `AbstractPlotting.Combined{AbstractPlotting.arc!}` are: 

```

```
