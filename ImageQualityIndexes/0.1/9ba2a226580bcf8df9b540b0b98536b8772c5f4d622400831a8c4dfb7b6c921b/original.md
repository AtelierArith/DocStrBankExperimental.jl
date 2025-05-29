```
abstract type FullReferenceIQI <: ImageQualityIndex
assess(::FullReferenceIQI, img, ref_img, args...)
```

Image quality index that requires its reference to be complete/full image or image series.

See also: [`ImageQualityIndex`](@ref), [`ReducedReferenceIQI`](@ref), [`NoReferenceIQI`](@ref)
