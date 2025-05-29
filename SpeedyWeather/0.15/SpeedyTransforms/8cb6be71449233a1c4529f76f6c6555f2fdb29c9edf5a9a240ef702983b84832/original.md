```julia
SpectralTransform(
    specs::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF, N, ArrayType};
    nlat_half,
    dealiasing,
    kwargs...
) -> SpeedyWeather.SpeedyTransforms.SpectralTransform{NF, _A, _B, _C, _D, _E, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF1, 1, _A1}, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF2, 2, _A2}} where {NF, _A, _B, _C, _D, _E, NF1, _A1, NF2, _A2}

```

Generator function for a `SpectralTransform` struct based on the size of the spectral coefficients `specs`. Use keyword arguments `nlat_half`, `Grid` or `deliasing` (if `nlat_half` not provided) to define the grid.
