aggregate(f::Function, ts::AbstractTimeSeries{T}, vt::AbstractVector{<:Union{Real,DateTime}}; order=0) where T <: Number

時系列 `ts` を `vt` の間隔で集約関数 `f` を使用して集約します。以下の順序オプションがあります：      (order=0) はリーマン積分を使用します     (order=1) は台形積分を使用します
