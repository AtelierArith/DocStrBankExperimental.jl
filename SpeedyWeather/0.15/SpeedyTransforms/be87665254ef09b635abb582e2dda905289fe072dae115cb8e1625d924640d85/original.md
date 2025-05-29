```julia
SpectralTransform(
    grids::SpeedyWeather.RingGrids.AbstractGridArray{NF, N, ArrayType};
    trunc,
    dealiasing,
    one_more_degree,
    kwargs...
) -> SpeedyWeather.SpeedyTransforms.SpectralTransform{NF, _A, _B, _C, _D, _E, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF1, 1, _A1}, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF2, 2, _A2}} where {NF, _A, _B, _C, _D, _E, NF1, _A1, NF2, _A2}

```

Generator function for a `SpectralTransform` struct based on the size and grid type of `grids`. Use keyword arugments `trunc`, `dealiasing` (ignored if `trunc` is used) or `one_more_degree` to define the spectral truncation.
