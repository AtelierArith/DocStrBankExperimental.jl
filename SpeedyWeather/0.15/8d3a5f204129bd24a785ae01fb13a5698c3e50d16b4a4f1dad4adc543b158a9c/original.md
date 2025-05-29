```julia
SpectralTransform(
    spectral_grid::SpeedyWeather.SpectralGrid;
    one_more_degree,
    kwargs...
) -> SpeedyWeather.SpeedyTransforms.SpectralTransform{NF, _A, _B, _C, _D, _E, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF1, 1, _A1}, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{NF2, 2, _A2}} where {NF<:AbstractFloat, _A, _B, _C, _D, _E, NF1<:AbstractFloat, _A1, NF2<:AbstractFloat, _A2}

```

Generator function for a SpectralTransform struct pulling in parameters from a SpectralGrid struct.
