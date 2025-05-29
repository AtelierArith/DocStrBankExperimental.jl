```
per_thread_stream()
```

Return a special object to use an implicit stream with per-thread synchronization behavior. This stream object is normally meant to be used with APIs that do not have per-thread versions of their APIs (i.e. without a `ptsz` or `ptds` suffix).

!!! note
    It is generally not needed to use this type of stream. With CUDA.jl, each task already gets its own non-blocking stream, and multithreading in Julia is typically accomplished using tasks.

