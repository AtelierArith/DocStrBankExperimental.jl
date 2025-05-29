```
materialize(lines::LineIndex, rows::Union{UnitRange{Int}, Vector{Int}} = 1:length(lines))
```

選択された `rows` の `Vector{NamedTuple}` を返します。`Tables.rowtable` に似ています。
