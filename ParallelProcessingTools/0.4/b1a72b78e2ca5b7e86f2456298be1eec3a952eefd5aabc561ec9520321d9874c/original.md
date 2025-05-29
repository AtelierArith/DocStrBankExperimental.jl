```
memory_limit()
```

Gets the virtual memory limit for the current Julia process.

Returns a tuple `(soft_limit::Int64, hard_limit::Int64)` (in units of bytes). Values of `-1` mean unlimited. 

!!! note
    Currently only works on Linux, simply returns `(Int64(-1), Int64(-1))` on other operationg systems.

