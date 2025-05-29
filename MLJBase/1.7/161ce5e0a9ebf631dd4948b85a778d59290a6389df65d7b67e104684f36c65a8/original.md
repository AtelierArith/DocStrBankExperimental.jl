```
fit!(N::Node;
     rows=nothing,
     verbosity=1,
     force=false,
     acceleration=CPU1())
```

Train all machines required to call the node `N`, in an appropriate order, but parallelizing where possible using specified `acceleration` mode.  These machines are those returned by `machines(N)`.

Supported modes of `acceleration`: `CPU1()`, `CPUThreads()`.
