```
XCBVoidFuture <: XCBFuture
```

Requests that generate no reply return `XCBVoidFuture`. When this future type is [`fetch`](@ref)ed, `fetch` returns `nothing`. Therefore, there is no difference between `fetch` and [`wait`](@ref) for this future type.
