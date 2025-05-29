```julia
struct ParabolicSegment{T} <: VLBISkyModels.GeometricModel{T}
```

A infinitely thin parabolic segment in the image domain. The segment is centered at zero, with roots ±1 and a yintercept of 1.

Note that if `T` isn't specified at construction then it defaults to `Float64`.
