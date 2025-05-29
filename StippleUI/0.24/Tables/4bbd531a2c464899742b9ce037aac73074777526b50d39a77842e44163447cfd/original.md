```
rowselection(dt::DataTable, idcolumn::Union{String, Symbol}, regex::Regex, cols = Colon())
```

Build a table selection based on a Regex.

```julia
rowselection(t, "b", r"hello|World")
```
