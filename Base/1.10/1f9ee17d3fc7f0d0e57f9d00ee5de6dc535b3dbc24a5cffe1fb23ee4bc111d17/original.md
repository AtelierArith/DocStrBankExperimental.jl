```
redirect_stderr([stream]) -> stream
```

Like [`redirect_stdout`](@ref), but for [`stderr`](@ref).

!!! note
    `stream` must be a compatible objects, such as an `IOStream`, `TTY`, `Pipe`, socket, or `devnull`.


See also [`redirect_stdio`](@ref).
