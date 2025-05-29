```
DeferredFuture(pid::Integer=myid()) -> DeferredFuture
```

Create a `DeferredFuture` on process `pid`. The default `pid` is the current process.

Note that the data in the `DeferredFuture` will still be located wherever it was `put!` from. The `pid` argument controlls where the outermost reference to that data is located.
