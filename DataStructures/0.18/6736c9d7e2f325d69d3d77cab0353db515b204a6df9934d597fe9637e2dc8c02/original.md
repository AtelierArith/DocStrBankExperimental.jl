```
packdeepcopy(sc)
```

This returns a packed copy of `sc` in which the keys and values are deep-copied. This function can be used to reclaim memory after many deletions. Time: O(*cn* log *n*)
