```julia
transform!(
    specs::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    grids::SpeedyWeather.RingGrids.AbstractGridArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

Spectral transform (grid to spectral space) from n-dimensional array of `grids` to an n-dimensional array `specs` of spherical harmonic coefficients. Uses FFT in the zonal direction, and a Legendre Transform in the meridional direction exploiting symmetries. The spectral transform is number format-flexible but `grids` and the spectral transform `S` have to have the same number format. Uses the precalculated arrays, FFT plans and other constants in the SpectralTransform struct `S`. The spectral transform is grid-flexible as long as the `typeof(grids)<:AbstractGridArray` and `S.Grid` matches.
