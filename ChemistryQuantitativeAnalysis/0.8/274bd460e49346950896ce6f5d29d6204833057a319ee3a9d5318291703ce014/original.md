```
samplename(dt::AbstractDataTable) -> Vector{Symbol}
samplename(at::AnalysisTable) -> Vector{Symbol}
```

Equivalent to `Symbol.(sampleobj(dt))` or `Symbol.(sampleobj(at))`.
