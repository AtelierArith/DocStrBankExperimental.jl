```
integrate(ts::AbstractTimeSeries{T}; order=0) where T
```

トレンドを持つ時系列を台形法（order=1）またはフラット法（order=0）を使用して統合します。
