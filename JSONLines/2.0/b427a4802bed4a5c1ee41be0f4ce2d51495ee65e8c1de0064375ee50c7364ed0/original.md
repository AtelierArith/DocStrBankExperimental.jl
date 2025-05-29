```
settypes!(lines::LineIndex, rows::Union{UnitRange{Int}, Vector{Int}} = 1:5)
```

Infer types of columns in `lines` based on `rows` selected. Overwrites existing types.
