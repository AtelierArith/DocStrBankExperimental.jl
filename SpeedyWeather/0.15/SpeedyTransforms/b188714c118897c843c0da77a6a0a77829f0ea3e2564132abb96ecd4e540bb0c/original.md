```julia
transform(
    specs::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform{NF};
    kwargs...
) -> Any

```

Spherical harmonic transform from `specs` to a newly allocated `grids::AbstractGridArray` using the precomputed spectral transform `S`.
