```
RotationMethod{T<:RotationType}
```

An abstract type representing a factor rotation method.

Each implementation of `M <: RotationMethod` must provide [`criterion_and_gradient!`](@ref) method.
