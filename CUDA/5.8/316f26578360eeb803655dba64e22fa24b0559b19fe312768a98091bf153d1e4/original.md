```
sync_threads_and(predicate)
```

Identical to `sync_threads()` with the additional feature that it evaluates predicate for all threads of the block and returns `true` if and only if `predicate` evaluates to `true` for all of them.
