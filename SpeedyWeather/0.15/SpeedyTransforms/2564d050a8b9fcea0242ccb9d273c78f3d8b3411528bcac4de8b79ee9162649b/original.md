```julia
power_spectrum(
    spec::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    normalize
) -> Any

```

Compute the power spectrum of the spherical harmonic coefficients `spec` (lower triangular matrix/array) of type `Complex{NF}`. For any additional dimensions in `spec`, the power spectrum is computed along the first/spherical harmonic dimension.
