```julia
struct Ring{T} <: VLBISkyModels.GeometricModel{T}
```

A infinitely thin ring model, whose expression in the image domain is     I(r,θ) = δ(r - 1)/2π i.e. a unit radius and flux delta ring.

By default if `T` isn't given, `Gaussian` defaults to `Float64`
