```
abstract type ReducedReferenceIQI <: ImageQualityIndex
assess(::ReducedReferenceIQI, img, ref_info, args...)
```

Image quality index that requires some information from reference image.

Different from [`FullReferenceIQI`](@ref), `ReducedReferenceIQI` doesn't need the complete reference image.

See also: [`ImageQualityIndex`](@ref), [`FullReferenceIQI`](@ref), [`NoReferenceIQI`](@ref)
