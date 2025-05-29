```
MseedTraceSegment(T, this_traceseg::MS3TraceSeg; headers_only=false) -> segment
```

Construct a `MseedTraceSegment{T}` from `MS3TraceSeg` object obtained from a call to one of `libmseed`'s functions.

If `headers_only` is `true`, then no data is wrapped and only header information is stored in the `segment` structure.
