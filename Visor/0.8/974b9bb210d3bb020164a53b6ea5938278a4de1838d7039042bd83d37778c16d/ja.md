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

プロセス名は `string(fn)` に設定されます。
