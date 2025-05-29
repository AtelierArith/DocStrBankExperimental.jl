```julia
sigqueue(pid, sig, val=0)
```

sends the signal `sig` to the process whose identifier is `pid`.  Argument `val` is an optional value to join to to the signal.  This value represents a C type `union sigval` (an union of a C `int` and a C `void*`), in Julia it is specified as an integer large enough to represent both kind of values.
