```julia
transform!(
    grids::SpeedyWeather.RingGrids.AbstractGridArray,
    specs::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    unscale_coslat
) -> SpeedyWeather.RingGrids.AbstractGridArray

```

Spectral transform (spectral to grid space) from n-dimensional array `specs` of spherical harmonic coefficients to an n-dimensional array `grids` of ring grids. Uses FFT in the zonal direction, and a Legendre Transform in the meridional direction exploiting symmetries. The spectral transform is number format-flexible but `grids` and the spectral transform `S` have to have the same number format. Uses the precalculated arrays, FFT plans and other constants in the SpectralTransform struct `S`. The spectral transform is grid-flexible as long as the `typeof(grids)<:AbstractGridArray` and `S.Grid` matches.
