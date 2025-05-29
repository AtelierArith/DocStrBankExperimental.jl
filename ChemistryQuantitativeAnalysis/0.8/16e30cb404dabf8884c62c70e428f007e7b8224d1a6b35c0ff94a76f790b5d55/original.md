```
getsample(dt::AnalyteDataTable, id::Int)
getsample(dt::SampleDataTable, id::Int)
getsample(dt::AnalyteDataTable, sample)
getsample(dt::SampleDataTable, sample)
```

Get data belonging to `sample` or `sampleobj(dt)[id]` as a `Vector`. For `SampleDataTable`, a new vector is created; mutating this vector will not change the value in `dt`.
