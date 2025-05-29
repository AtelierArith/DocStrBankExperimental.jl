```
integrate(ts::AbstractTimeSeries{T}, Δt::TimeInterval, indhint=firstindex(ts); order=0) where T <: Number
```

時間間隔Δtにわたって時系列を統合します。台形法（order=1）またはフラット法（order=0）を使用します。
