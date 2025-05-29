```
MseedTraceList(mstl::Ref{Ptr{MS3TraceList}}; headers_only=false)
```

Construct a `MseedTraceList` from a reference to a `MS3TraceList` struct obtained from a call to one of `libmseed`'s functions.

This function builds a full `MseedTraceList` and copies the data from `mstl`, unless `headers_only` is `true`, in which case data is not copied.
