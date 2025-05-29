```
eachanalyte(dt::AbstractDataTable)
```

Create an iterator which gets data belonging to each analyte as a `Vector`. For `AnalyteDataTable`, new vectors are created; mutating these vector will not change the value in `dt`.
