```
SpanContext(;span_id, trace_id, is_remote, trace_flag=TraceFlag(), trace_state=TraceState())
```

A `SpanContext` represents the portion of a `Span` which must be serialized and propagated along side of a distributed context. `SpanContext`s are immutable.

The OpenTelemetry `SpanContext` representation conforms to the [W3C TraceContext specification](https://www.w3.org/TR/trace-context/). It contains two identifiers - a `TraceId` and a `SpanId` - along with a set of common `TraceFlags` and system-specific `TraceState` values.

`TraceId` A valid trace identifier is a 16-byte array with at least one non-zero byte.

`SpanId` A valid span identifier is an 8-byte array with at least one non-zero byte.

`TraceFlags` contain details about the trace. Unlike TraceState values, TraceFlags are present in all traces. The current version of the specification only supports a single flag called [sampled](https://www.w3.org/TR/trace-context/#sampled-flag).

`TraceState` carries vendor-specific trace identification data, represented as a list of key-value pairs. TraceState allows multiple tracing systems to participate in the same trace. It is fully described in the [W3C Trace Context specification](https://www.w3.org/TR/trace-context/#tracestate-header).
