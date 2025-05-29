```
oneof_field_types(::Type{T}) where T
```

Return a named tuple of `oneof` field names to the full NamedTuple type describing the type individual `oneof` options. Returns an empty named tuple, `(;)`, if the original proto message doesn't contain any `oneof` fields
