```
rowselection(dt::DataTable, idcolumn::Union{String, Symbol}, values, cols = Colon())
```

Build a table selection based on an index and a value / list of values.

```
rowselection(dt, "a", [1, 3])
rowselection(dt, "a", 2:9)
```
