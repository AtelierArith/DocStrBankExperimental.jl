```
SampleDataTable(analyte::AbstractVector, samplecol::Symbol, table)
SampleDataTable(table, analytename::AbstractVector, samplecol::Symbol)
```

An interface equivalent to `SampleDataTable(analyte, getproperty(table, samplecol), samplecol, table)`.
