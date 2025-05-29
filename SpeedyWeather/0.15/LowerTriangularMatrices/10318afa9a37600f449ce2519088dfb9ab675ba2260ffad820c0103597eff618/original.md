```julia
eachmatrix(
    L1::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    Ls::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray...
) -> Any

```

Iterator for the non-horizontal dimensions in LowerTriangularArrays. Checks that the LowerTriangularArrays match according to `lowertriangular_match`.
