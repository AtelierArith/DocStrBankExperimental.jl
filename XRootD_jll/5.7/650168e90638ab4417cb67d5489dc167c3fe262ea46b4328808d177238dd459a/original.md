```
xrdcp(; adjust_PATH::Bool=true, adjust_LIBPATH::Bool=true) -> Cmd
```

An `ExecutableProduct` wrapper that supports the execution of xrdcp. This wrapper is thread-safe and should be preferred on Julia 1.6+.

# Example

```julia
run(`$(xrdcp()) $arguments`)
```

!!! compat "Julia 1.6"
    This method requires Julia version 1.6 or newer.

