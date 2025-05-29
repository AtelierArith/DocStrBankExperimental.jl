```
allocframe(io)
```

Allocate memory for one frame of JavaSeis dataset.  Returns `(Array{Float32,2},Array{UInt8,2})`. For example, `trcs, hdrs = allocframe(jsopen("data.js"))`.
