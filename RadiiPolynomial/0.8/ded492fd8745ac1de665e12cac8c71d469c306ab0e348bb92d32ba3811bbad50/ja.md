```
(𝒟::Derivative)(a::AbstractSequence)
```

`a`の`order(𝒟)`-階微分を計算します。これは`differentiate(a, order(𝒟))`と同等です。

関連情報: [`*(::Derivative, ::AbstractSequence)`](@ref), [`Derivative`](@ref), [`differentiate`](@ref) および [`differentiate!`](@ref)。
