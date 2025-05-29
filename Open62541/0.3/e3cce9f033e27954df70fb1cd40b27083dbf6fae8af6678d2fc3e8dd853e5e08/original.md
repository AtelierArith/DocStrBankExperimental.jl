```
Int64_new()::Ptr{Int64}
```

creates and initializes ("zeros") a `Int64` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Int64_delete(x::Ptr{Int64})`
