```
Int32_new()::Ptr{Int32}
```

creates and initializes ("zeros") a `Int32` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Int32_delete(x::Ptr{Int32})`
