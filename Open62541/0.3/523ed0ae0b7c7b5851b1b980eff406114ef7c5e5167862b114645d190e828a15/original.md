```
Float32_new()::Ptr{Float32}
```

creates and initializes ("zeros") a `Float32` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Float32_delete(x::Ptr{Float32})`
