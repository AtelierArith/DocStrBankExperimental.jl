```
TraceState(entries::Pair{String,String}...)
```

`TraceState`は、ベンダー固有のトレース識別データを保持し、キーと値のペアのリストとして表現されます。`TraceState`は、複数のトレースシステムが同じトレースに参加できるようにします。これは、[W3C Trace Context specification](https://www.w3.org/TR/trace-context/#tracestate-header)で完全に説明されています。
