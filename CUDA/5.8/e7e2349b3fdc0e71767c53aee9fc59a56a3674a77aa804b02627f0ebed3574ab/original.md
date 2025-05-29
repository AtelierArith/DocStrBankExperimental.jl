```
sync_threads_count(predicate)
```

Identical to `sync_threads()` with the additional feature that it evaluates predicate for all threads of the block and returns the number of threads for which `predicate` evaluates to true.
