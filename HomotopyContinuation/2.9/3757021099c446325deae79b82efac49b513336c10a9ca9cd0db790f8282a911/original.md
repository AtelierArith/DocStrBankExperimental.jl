```
parameter_homotopy(F; start_parameters, target_parameters)
```

Construct a [`ParameterHomotopy`](@ref). If `F` is homogeneous, then a random affine chart is chosen (via [`AffineChartHomotopy`](@ref)).
