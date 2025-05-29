```
average(ts::AbstractTimeSeries{T}, Δt::TimeInterval; indhint=nothing, order=0) where T <: Number
```

時間間隔Δtにわたって時系列を積分します。台形法（order=1）またはフラット法（order=0）を使用します。最後に、積分をΔtの経過時間で割ります。
