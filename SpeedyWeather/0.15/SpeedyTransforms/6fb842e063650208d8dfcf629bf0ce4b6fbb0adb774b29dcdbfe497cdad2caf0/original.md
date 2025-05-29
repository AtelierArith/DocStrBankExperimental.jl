```julia
∇²(
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    kwargs...
) -> Any

```

Returns the Laplace operator ∇² applied to input `alms`. Acts on the unit sphere, i.e. it omits 1/radius^2 scaling unless `radius` keyword argument is provided.
