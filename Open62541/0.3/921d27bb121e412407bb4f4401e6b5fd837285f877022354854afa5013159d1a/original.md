```
Int8_new()::Ptr{Int8}
```

creates and initializes ("zeros") a `Int8` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Int8_delete(x::Ptr{Int8})`
