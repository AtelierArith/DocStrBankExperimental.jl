```
UA_STRING(s::AbstractString)::Ptr{UA_String}
```

creates a `UA_String` object from `s`. Memory is allocated by C and needs to be cleaned up with `UA_String_delete(x::Ptr{UA_String})`.
