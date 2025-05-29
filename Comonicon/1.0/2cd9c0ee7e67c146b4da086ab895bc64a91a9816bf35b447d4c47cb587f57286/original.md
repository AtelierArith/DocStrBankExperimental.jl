```
@lazyload expr @cast <valid castable expr>
```

Evaluate `expr` if command `f` is called. This is useful for reducing the latency of scripts that has subcmds depend on plotting, serialization etc.

Please see [`@cast`](@ref) for valid expression specifications.

!!! warning
    This macro only works at top-level command and thus can only be used in `Main` and only works in scripts. Using this macro in any other module or a project module will not work.

