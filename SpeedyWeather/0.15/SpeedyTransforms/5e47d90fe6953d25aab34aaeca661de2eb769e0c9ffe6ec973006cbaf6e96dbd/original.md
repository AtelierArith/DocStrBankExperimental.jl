```julia
transform(
    grids::SpeedyWeather.RingGrids.AbstractGridArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform{NF}
) -> Any

```

Spherical harmonic transform from `grids` to a newly allocated `specs::LowerTriangularArray` using the precomputed spectral transform `S`.
