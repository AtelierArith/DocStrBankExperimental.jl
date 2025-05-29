```
UInt32_new()::Ptr{UInt32}
```

creates and initializes ("zeros") a `UInt32` object whose memory is allocated by C. After use, it needs to be  cleaned up with `UInt32_delete(x::Ptr{UInt32})`
