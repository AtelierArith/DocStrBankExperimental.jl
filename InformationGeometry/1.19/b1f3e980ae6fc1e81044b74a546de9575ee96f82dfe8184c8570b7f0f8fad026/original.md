```
IntegrateND(F::Function,Cube::HyperCube; tol::Real=1e-12, WE::Bool=false, kwargs...)
```

Integrates the function `F` over `Cube` with the help of **HCubature.jl** to a tolerance of `tol`. If `WE=true`, the result is returned as a `Measurement` which also contains the estimated error in the result.
