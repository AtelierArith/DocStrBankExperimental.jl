```
UA_BYTESTRING_ALLOC(s::AbstractString)::Ptr{UA_String}
```

creates a `UA_ByteString` object from `s`. Memory is allocated by C and needs to be cleaned up with `UA_ByteString_delete(x::Ptr{UA_ByteString})`.
