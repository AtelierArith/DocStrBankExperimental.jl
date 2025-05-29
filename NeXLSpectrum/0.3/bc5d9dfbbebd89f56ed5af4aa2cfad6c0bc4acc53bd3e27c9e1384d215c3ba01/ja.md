```
χ²(s1::Spectrum{T}, s2::Spectrum{U}, chs)::T where {T<:Real, U <: Real}
χ²(specs::AbstractArray{Spectrum{T}}, chs)::Matrix{T}
```

`s1`と`s2`の間のチャネル`chs`にわたる線量補正された縮小χ²メトリックを計算します。

2番目の形式は、配列内の各スペクトルを他のスペクトルと比較するχ²の行列を計算します。
