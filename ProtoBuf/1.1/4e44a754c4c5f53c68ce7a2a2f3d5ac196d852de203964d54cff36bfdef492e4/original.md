```
default_values(::Type{T}) where T
```

Return a named tuple of fields names to their respective default values from the original proto message type. Fields of `OneOf` types are expanded as they don't map to any single default value.

`required` message-fields do not have a default value and are represented as `Ref{MyFieldMessageType}()`.
