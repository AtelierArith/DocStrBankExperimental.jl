```
rowselection(dt::DataTable, idcolumn::Union{String, Symbol}, f::Function, cols = Colon())
```

Build a table selection based on a function.

```
rowselection(dt, "a", iseven)
rowselection(dt, "a", x -> x > 3)
```
