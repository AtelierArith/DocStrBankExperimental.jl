```
interpolate(f_extrap::Function, ts::AbstractTimeSeries, vt::AbstractVector{<:Real}; indhint=nothing)
```

タイムシリーズ ts::AbstractTimeSeries をタイムスタンプ vt::AbstractVector{<:Real} で補間します。現在サポートされている二点アルゴリズムは、ゼロ次保持法と一次補間です。
