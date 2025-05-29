```
averages(ts::AbstractTimeSeries{T}, vt::AbstractVector{<:Real}; order=0) where T
```

vtの区間間のN-1の時間加重平均のベクトルを返します。 (order=0) はリーマン積分を使用し、(order=1) は台形積分を使用します。
