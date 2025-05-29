```
Float64_new()::Ptr{Float64}
```

creates and initializes ("zeros") a `Float64` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Float64_delete(x::Ptr{Float64})`
