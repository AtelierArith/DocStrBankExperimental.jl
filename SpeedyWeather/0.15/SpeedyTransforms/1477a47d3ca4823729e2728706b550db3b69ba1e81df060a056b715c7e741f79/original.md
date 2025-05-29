```julia
divergence(
    u::SpeedyWeather.RingGrids.AbstractGridArray,
    v::SpeedyWeather.RingGrids.AbstractGridArray;
    kwargs...
) -> Any

```

Divergence (∇⋅) of two vector components `u, v` on a grid. Applies 1/coslat scaling, transforms to spectral space and returns the spectral divergence. Acts on the unit sphere, i.e. it omits 1/radius scaling unless `radius` keyword argument is provided.
