```
Bool_new()::Ptr{Bool}
```

creates and initializes ("zeros") a `Bool` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Bool_delete(x::Ptr{Bool})`
