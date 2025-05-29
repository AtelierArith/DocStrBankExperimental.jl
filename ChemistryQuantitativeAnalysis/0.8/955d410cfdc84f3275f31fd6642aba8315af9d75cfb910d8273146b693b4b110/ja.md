```
sampleobj(dt::AbstractDataTable{A, S}) -> Vector{S}
sampleobj(at::AnalysisTable{A, S, T}) -> Vector{S}
```

`getfield(dt, :sample)` または `getfield(at, :sample)` と同等です。
