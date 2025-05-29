```
fused(f, args...; kwargs...)
```

This function decorator modifies `f` to fuse the contained array operations and optimize the resulting program. The function must return a single array or tuple of arrays.  Some keyword arguments can be passed to control the execution of the program:     - `verbose=false`: Print the generated code before execution     - `tag=:global`: A tag to distinguish between different classes of inputs for the same program.
