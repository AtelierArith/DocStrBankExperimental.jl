```julia
transform(
    grids::SpeedyWeather.RingGrids.AbstractGridArray;
    kwargs...
) -> Any

```

Spectral transform (grid to spectral space) from `grids` to a newly allocated `LowerTriangularArray`. Based on the size of `grids` and the keyword `dealiasing` the spectral resolution trunc is retrieved. SpectralTransform struct `S` is allocated to execute `transform(grids, S)`.
