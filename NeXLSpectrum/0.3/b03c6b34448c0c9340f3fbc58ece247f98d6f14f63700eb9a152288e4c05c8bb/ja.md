```
detect(emitted::Dict{<:XRay,<:Real}, det::EDSDetector, response::Matrix{Float64}; noise=false)
```

指定された検出器で `emitted` の強度が検出されたかのようにスペクトルを返します。`noise=true` は、結果として得られる測定された `Spectrum` にポアソンノイズを追加します。
