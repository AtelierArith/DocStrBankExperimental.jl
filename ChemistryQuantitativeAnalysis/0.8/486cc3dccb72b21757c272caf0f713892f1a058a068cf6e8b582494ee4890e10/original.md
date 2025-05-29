```
getanalyte(dt::AnalyteDataTable, id::Int)
getanalyte(dt::SampleDataTable, id::Int)
getanalyte(dt::AnalyteDataTable, analyte)
getanalyte(dt::SampleDataTable, analyte)
```

Get data belonging to `analyte` or `analyteobj(dt)[id]` as a `Vector`. For `AnalyteDataTable`, a new vector is created; mutating this vector will not change the value in `dt`.
