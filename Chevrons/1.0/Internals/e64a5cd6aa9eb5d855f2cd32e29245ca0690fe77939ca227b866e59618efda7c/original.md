```
enable_repl(on::Bool=true)
```

Enable or disable REPL integration.

When enabled, all commands in the REPL are transformed by [`chevrons`](@ref).

You can call this in your `startup.jl` file.
