```
reconcile!(p::Path, n::Integer=1)
```

Reconcile all inconsistencies in a path starting from index `n`. Used internally whenever segments are inserted into the path, but can be safely used by the user as well.
