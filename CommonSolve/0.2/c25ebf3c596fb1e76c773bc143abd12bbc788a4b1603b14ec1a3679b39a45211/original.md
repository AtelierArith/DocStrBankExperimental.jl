```julia
CommonSolve.step!(iter, args...; kwargs...)
```

Progress the iterator object (the one returned by `CommonSolve.init`). The additional arguments typically describe how much to progress the iterator for, and are implementation-specific.
