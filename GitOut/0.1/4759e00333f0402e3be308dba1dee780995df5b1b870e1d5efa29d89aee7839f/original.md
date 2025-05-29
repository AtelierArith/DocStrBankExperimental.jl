```julia
rungit(::Type{Base.Process}; ...) -> Any
rungit(
    ::Type{Base.Process},
    args;
    stdin,
    stdout,
    stderr,
    append,
    wait,
    verbose_debug_logs,
    kw...
) -> Any

```

Runs the command created by [`git`](@ref).

## Keyword Arguments

  * `stdin=devnull`: the `stdin` of the process.
  * `stdout=devnull`: the `stdout` of the process.
  * `stderr=nothing`: the `stdout` of the process.  If `nothing`, a buffer will be created and used for   error reporting.  So, for example, setting this to `devnull` will prevent showing the `stderr` in errors.
  * `append=false`: Controls whether file output is appended to a file if `stdout` or `stderr` are set to a file.
  * `wait=true`: Whether the thread should block until the process returns.
  * `verbose_debug_logs=true`: If `stderr=nothing`, use a buffer to create a `@debug` log.

Additional keyword arguments are passed to [`git`](@ref).
