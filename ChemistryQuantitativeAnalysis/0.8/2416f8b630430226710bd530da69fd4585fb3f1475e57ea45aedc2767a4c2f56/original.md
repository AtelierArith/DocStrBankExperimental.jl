```
analytename(dt::AbstractDataTable) -> Vector{Symbol}
analytename(at::AnalysisTable) -> Vector{Symbol}
```

Equivalent to `Symbol.(analyteobj(dt))` or `Symbol.(analyteobj(at))`.
