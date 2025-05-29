```
process(fn;
        args=(),
        namedargs=(;),
        force_interrupt_after::Real=1.0,
        stop_waiting_after::Real=Inf,
        debounce_time=NaN,
        thread=true,
        restart=:transient)::ProcessSpec
```

The process name is set equals to `string(fn)`.
