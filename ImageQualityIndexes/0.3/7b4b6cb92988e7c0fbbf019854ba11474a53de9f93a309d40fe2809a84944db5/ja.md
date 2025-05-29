```
abstract type ReducedReferenceIQI <: ImageQualityIndex
assess(::ReducedReferenceIQI, img, ref_info, args...)
```

参照画像からの情報を必要とする画像品質指標です。

[`FullReferenceIQI`](@ref)とは異なり、`ReducedReferenceIQI`は完全な参照画像を必要としません。

関連情報: [`ImageQualityIndex`](@ref), [`FullReferenceIQI`](@ref), [`NoReferenceIQI`](@ref)
