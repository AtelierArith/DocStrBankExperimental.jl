```
integrate(ts::AbstractTimeSeries{T}, vt::AbstractVector{<:Real}; order=1) where T
```

vの区間で制約されたN-1の積分のベクトルを返します。以下の順序オプションがあります：      (order=0) はリーマン積分を使用します     (order=1) は台形積分を使用します
