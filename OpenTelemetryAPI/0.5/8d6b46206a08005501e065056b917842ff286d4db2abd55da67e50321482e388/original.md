```
TraceState(entries::Pair{String,String}...)
```

`TraceState` carries vendor-specific trace identification data, represented as a list of key-value pairs. `TraceState` allows multiple tracing systems to participate in the same trace. It is fully described in the [W3C Trace Context specification](https://www.w3.org/TR/trace-context/#tracestate-header).
