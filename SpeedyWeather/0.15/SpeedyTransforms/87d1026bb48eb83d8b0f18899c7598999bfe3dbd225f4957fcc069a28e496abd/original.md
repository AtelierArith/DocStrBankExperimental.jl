```julia
SpectralTransform(
    grids::SpeedyWeather.RingGrids.AbstractGridArray{NF1, N, ArrayType1},
    specs::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF2, N, ArrayType2};
    kwargs...
) -> SpeedyWeather.SpeedyTransforms.SpectralTransform{NF, _A, _B, _C, _D, _E, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF1, 1, _A1}, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF2, 2, _A2}} where {NF, _A, _B, _C, _D, _E, NF1, _A1, NF2, _A2}

```

Generator function for a `SpectralTransform` struct to transform between `grids` and `specs`.
