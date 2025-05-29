```
analyteobj(dt::AbstractDataTable{A}) -> Vector{A}
analyteobj(at::AnalysisTable{A}) -> Vector{A}
```

`getfield(dt, :analyte)` または `getfield(at, :analyte)` と同等です。
