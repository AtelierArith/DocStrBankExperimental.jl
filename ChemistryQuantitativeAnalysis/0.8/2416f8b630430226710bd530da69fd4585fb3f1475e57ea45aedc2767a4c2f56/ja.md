```
analytename(dt::AbstractDataTable) -> Vector{Symbol}
analytename(at::AnalysisTable) -> Vector{Symbol}
```

`Symbol.(analyteobj(dt))` または `Symbol.(analyteobj(at))` と同等です。
