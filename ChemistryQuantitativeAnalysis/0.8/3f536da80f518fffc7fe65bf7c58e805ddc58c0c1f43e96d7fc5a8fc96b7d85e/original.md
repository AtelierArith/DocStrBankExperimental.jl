```
AnalyteDataTable(analytecol::Symbol, samplename::AbstractVector, table)
AnalyteDataTable(table, analytecol::Symbol, samplename::AbstractVector)
```

An interface equivalent to `AnalyteDataTable(getproperty(table, analytecol), samplename, analytecol, table)`.
