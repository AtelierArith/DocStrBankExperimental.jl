```
pseed!(s::Int)
```

Seed each of the thread local RNGs with `s*threadid()` to get  reproducible, but different random number sequences on each thread.
