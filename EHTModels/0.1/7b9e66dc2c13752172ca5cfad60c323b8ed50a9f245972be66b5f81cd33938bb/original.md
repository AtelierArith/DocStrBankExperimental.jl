```julia
struct Gaussian{T} <: EHTModels.GeometricModel
```

Gaussian with unit standard deviation and flux. By default if T isn't given, `Gaussian` defaults to `Float64`
