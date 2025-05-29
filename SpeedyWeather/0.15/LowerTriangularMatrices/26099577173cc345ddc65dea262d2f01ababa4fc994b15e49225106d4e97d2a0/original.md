```julia
eachharmonic(
    L::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray
) -> Any

```

creates `unit_range::UnitRange` to loop over all non-zeros/spherical harmonics numbers in a LowerTriangularArray `L`. Like `eachindex` but skips the upper triangle with zeros in `L`.
