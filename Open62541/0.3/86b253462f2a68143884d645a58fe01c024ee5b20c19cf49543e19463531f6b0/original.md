```
UInt16_new()::Ptr{UInt16}
```

creates and initializes ("zeros") a `UInt16` object whose memory is allocated by C. After use, it needs to be  cleaned up with `UInt16_delete(x::Ptr{UInt16})`
