```
strictinterp(f_interp::Function, ts::AbstractTimeSeries, vt::AbstractVector{<:Real}; indhint=nothing)
```

TimeSeries ts::AbstractTimeSeriesを、二点補間アルゴリズムf_interpを使用して、タイムスタンプvt::AbstractVector{<:Real}で補間します。タイムスタンプがタイムシリーズの区間内にない場合は、'missing'が返されます。現在サポートされている二点アルゴリズムは、ゼロ次保持、一次補間です。
