```
DeferredChannel(pid::Integer=myid(), num::Integer=1; content::DataType=Any) -> DeferredChannel
```

Create a `DeferredChannel`. The default `pid` is the current process. When initialized, the `DeferredChannel` will reference a `Channel{content}(num)` on process `pid`.

Note that the data in the `DeferredChannel` will still be located wherever the first piece of data was `put!` from. The `pid` argument controls where the outermost reference to that data is located.
