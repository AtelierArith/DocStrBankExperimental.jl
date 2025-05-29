```
StackFrames(::Type{T}=Float32, d::Int...)
```

Use a pre-initialized `CircularArrayBuffer` to store the latest several states specified by `d`. Before processing any observation, the buffer is filled with `zero{T} by default.
