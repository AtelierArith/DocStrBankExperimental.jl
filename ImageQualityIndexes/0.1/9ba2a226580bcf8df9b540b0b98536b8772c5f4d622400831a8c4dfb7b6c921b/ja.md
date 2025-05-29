```
abstract type FullReferenceIQI <: ImageQualityIndex
assess(::FullReferenceIQI, img, ref_img, args...)
```

完全参照画像品質指標で、参照が完全な画像または画像シリーズであることを要求します。

参照: [`ImageQualityIndex`](@ref), [`ReducedReferenceIQI`](@ref), [`NoReferenceIQI`](@ref)
