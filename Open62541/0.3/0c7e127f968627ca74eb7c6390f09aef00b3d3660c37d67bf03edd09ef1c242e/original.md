```
Int16_new()::Ptr{Int16}
```

creates and initializes ("zeros") a `Int16` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Int16_delete(x::Ptr{Int16})`
