```julia
∇⁻²(
    ∇²alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    kwargs...
) -> Any

```

Returns the inverse Laplace operator ∇⁻² applied to input `alms`. Acts on the unit sphere, i.e. it omits radius^2 scaling unless `radius` keyword argument is provided.
