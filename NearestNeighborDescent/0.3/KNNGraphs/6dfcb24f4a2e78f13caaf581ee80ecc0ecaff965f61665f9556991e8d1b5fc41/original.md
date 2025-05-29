```
update_flag!(g::LockHeapKNNGraph, i, j, flag)
```

Update the flag of the edge at the given indices. Since the flags don't influence the edge ordering, this can't invalidate the heap invariant. Uses locks to ensure thread safety.
