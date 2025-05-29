```
process(id, fn;
        args=(),
        namedargs=(;),
        force_interrupt_after::Real=1.0,
        stop_waiting_after::Real=Inf,
        debounce_time=NaN,
        trace_exception=false,
        thread=true,
        restart=:transient)::ProcessSpec
```

Declare a supervised task that may be forcibly interrupted.

`id` is the process name and `fn` is the task function.

`process` returns only a specification: the task function has to be started with [`supervise`](@ref).

See [`process`](@ref) online docs for more details.
