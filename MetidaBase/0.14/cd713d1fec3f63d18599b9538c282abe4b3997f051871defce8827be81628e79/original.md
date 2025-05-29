```
metida_table(args...; kwargs...)
```

Make MetidaTable.

For AbstractIDResult:

```
metida_table(obj::DataSet{RD}; order = nothing, results = nothing, ids = nothing)
```

Where obj <: DataSet{<:AbstractIDResult} order - order of columns (Vector of column's names); results - result columns; ids - ID's columns;
