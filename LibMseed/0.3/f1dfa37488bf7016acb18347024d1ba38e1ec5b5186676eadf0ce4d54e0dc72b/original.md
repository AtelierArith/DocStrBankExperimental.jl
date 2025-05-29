```
MseedTraceID(this_traceid::MS3TraceID; headers_only=false)
```

Construct a `MseedTraceID` from a `MS3TraceID` object, obtained from a call to one of `libmseed`'s functions.

If `headers_only` is `true`, then the data is not read, only trace information.
