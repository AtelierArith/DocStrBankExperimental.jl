```julia
eachharmonic(
    L1::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    Ls::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray...
) -> Any

```

creates `unit_range::UnitRange` to loop over all non-zeros in the LowerTriangularMatrices provided as arguments. Checks bounds first. All LowerTriangularMatrix's need to be of the same size. Like `eachindex` but skips the upper triangle with zeros in `L`.
