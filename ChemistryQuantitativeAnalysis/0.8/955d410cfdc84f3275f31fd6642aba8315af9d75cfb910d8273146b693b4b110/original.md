```
sampleobj(dt::AbstractDataTable{A, S}) -> Vector{S}
sampleobj(at::AnalysisTable{A, S, T}) -> Vector{S}
```

Equivalent to `getfield(dt, :sample)` or `getfield(at, :sample)`.
