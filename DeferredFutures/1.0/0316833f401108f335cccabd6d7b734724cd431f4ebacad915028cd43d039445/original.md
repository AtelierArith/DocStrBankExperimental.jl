```
DeferredChannel(pid::Integer=myid(), num::Integer=1; content::DataType=Any) -> DeferredChannel
```

Create a `DeferredChannel` with a reference to a remote channel of a specific size and type. f() is a function that when executed on `pid` must return an implementation of an `AbstractChannel`.

The default `pid` is the current process.
