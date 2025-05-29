```
context([id::UInt], [container])
```

Get a new context object.  If `id` is not passed, then return a global context for the current thread/task.  The `container` must be an object that supports `push!`, `getindex`, `empty!`, and `length` functions. The default is `Dict{Any,Any}`.
