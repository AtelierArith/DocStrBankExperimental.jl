```
isvalid_pid(pid::Int)::Bool
```

Tests if `pid` is a valid Julia process ID.

Equivalent to `pid in Distributed.procs()`, but faster.
