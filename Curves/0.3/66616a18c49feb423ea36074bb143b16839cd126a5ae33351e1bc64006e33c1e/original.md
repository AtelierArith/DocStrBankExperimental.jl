```
interpolate(xval:: AbstractArray{T} where T, c1:: Curve; kwargs...):: Curve
```

Interpolates the curve onto the given array and returns a new Curve instance on the interpolated points.

The output Curve is constructed using default settings, alternative settings can be passed to the Curve constructor using the ˋkwargs...ˋ
