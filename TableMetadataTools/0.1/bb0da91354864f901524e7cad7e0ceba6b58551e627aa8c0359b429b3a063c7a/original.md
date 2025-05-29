```
setcolmetadatastyle!([predicate], table; style::Symbol=:note, [col::Symbol])
```

Set style for column-level keys in `table` that match `predicate` to `style`. If `predicate` is omitted then all metadata is updated. If `col` is passed then it must be a column name and only metadata for this column is updated (if present).

See also: [`setmetadatastyle`!](@ref), [`setallmetadatastyle!](@ref)
