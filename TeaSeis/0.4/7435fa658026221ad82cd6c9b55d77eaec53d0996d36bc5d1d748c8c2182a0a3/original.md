```
set!(prop, hdrs, i, value)
```

Set the value of the trace property `prop::TraceProperty` stored in the header of the ith column of `hdrs::Array{UInt8,2}` to `value::T`.  For example, `io=jsopen("test.js"); hdrs=readframehdrs(io,1); set!(prop(io,"REC_X"), 1, 10.0)`.
