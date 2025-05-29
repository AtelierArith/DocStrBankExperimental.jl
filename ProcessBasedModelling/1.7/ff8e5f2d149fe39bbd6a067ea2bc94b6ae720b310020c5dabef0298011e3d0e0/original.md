```
register_default_process!(process, m::Module; warn = true)
```

Register a `process` (`Equation` or `Process`) as a default process for its LHS variable in the list of default processes tracked by the given module. If `warn`, throw a warning if a default process with same LHS variable already exists and will be overwritten.

You can use [`default_processes`](@ref) to obtain the list of tracked default processes.

!!! note "For developers"
    If you are developing a new module/package that is based on ProcessBasedModelling.jl, and within it you also register default processes, then enclose your `register_default_process!` calls within the module's `__init__()` function. For example:

    ```julia
    module MyProcesses
    # ...

    function __init__()
        register_default_process!.(
            [
                process1,
                process2,
                # ...
            ],
            Ref(MyProcesses)
        )
    end

    end # module
    ```

