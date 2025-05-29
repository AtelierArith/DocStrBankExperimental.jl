```
interpolate(ts::AbstractTimeSeries, t::Union{<:Real, AbstractVector{<:Real}}; order=0)
```

時系列 ts::AbstractTimeSeries を、時刻 vt::AbstractVector{Real} で補間します。vt に対応する値のベクトルを返します。キーワード "order" はアルゴリズムを選択します：ゼロ次保持 (order=0) と一次補間 (order=1) をサポートしています。
