```
abstract type NoReferenceIQI <: ImageQualityIndex
assess(::NoReferenceIQI, img, args...)
```

情報を必要としない画像品質指標。

参照: [`ImageQualityIndex`](@ref), [`FullReferenceIQI`](@ref), [`ReducedReferenceIQI`](@ref)
