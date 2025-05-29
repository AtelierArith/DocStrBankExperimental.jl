```
UInt8_new()::Ptr{UInt8}
```

creates and initializes ("zeros") a `UInt8` object whose memory is allocated by C. After use, it needs to be  cleaned up with `UInt8_delete(x::Ptr{UInt8})`
