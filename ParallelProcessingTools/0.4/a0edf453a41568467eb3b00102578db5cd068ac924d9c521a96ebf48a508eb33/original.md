```
memory_limit!(soft_limit::Integer, hard_limit::Integer = -1)
```

Sets the virtual memory limit for the current Julia process.

`soft_limit` and `hard_limit` are in units of bytes. Values of `-1` mean unlimited. `hard_limit` must not be stricter than `soft_limit`, and should typically be set to `-1`.

Returns `(soft_limit::Int64, hard_limit::Int64)`.

!!! note
    Currently only has an effect on Linux, does nothing and simply returns `(Int64(-1), Int64(-1))` on other operating systems.

