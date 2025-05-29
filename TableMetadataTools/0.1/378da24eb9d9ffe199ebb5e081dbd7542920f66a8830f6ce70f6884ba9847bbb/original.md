```
setallmetadatastyle!([predicate], table; style::Symbol=:note)
```

Set style for table-level and column-level keys in `table` that match `predicate` to `style`. If `predicate` is omitted then all metadata is updated.

See also: [`setmetadatastyle`!](@ref), [`setcolmetadatastyle!](@ref)
