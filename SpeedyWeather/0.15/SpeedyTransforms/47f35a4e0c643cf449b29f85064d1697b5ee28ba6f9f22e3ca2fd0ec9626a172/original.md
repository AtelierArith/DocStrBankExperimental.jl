```julia
∇⁻²!(
    ∇⁻²alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    add,
    flipsign,
    kwargs...
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

Calls `∇²!(∇⁻²alms, alms, S; add, flipsign, inverse=true)`.
