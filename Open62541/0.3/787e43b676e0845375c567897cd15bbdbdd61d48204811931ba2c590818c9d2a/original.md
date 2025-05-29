```
UInt64_new()::Ptr{UInt64}
```

creates and initializes ("zeros") a `UInt64` object whose memory is allocated by C. After use, it needs to be  cleaned up with `UInt64_delete(x::Ptr{UInt64})`
