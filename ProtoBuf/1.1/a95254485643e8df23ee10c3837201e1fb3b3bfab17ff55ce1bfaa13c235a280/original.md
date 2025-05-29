```
field_numbers(::Type{T}) where T
```

Return a named tuple of fields names to their respective field numbers from the original proto message type. Fields of `OneOf` types are expanded as they don't map to any single field number.
