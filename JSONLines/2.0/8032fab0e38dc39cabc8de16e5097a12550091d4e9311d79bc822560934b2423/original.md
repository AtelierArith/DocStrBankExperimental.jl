```
materialize(lines::LineIndex, rows::Union{UnitRange{Int}, Vector{Int}} = 1:length(lines))
```

Return a `Vector{NamedTuple}` of the `rows` selected. Similar to `Tables.rowtable`
