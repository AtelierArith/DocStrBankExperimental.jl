```
abstract type NoReferenceIQI <: ImageQualityIndex
assess(::NoReferenceIQI, img, args...)
```

Image quality index that doesn't require any information.

See also: [`ImageQualityIndex`](@ref), [`FullReferenceIQI`](@ref), [`ReducedReferenceIQI`](@ref)
