```
analyteobj(dt::AbstractDataTable{A}) -> Vector{A}
analyteobj(at::AnalysisTable{A}) -> Vector{A}
```

Equivalent to `getfield(dt, :analyte)` or `getfield(at, :analyte)`.
