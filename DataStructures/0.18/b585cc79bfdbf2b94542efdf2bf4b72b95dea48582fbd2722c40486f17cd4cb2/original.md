```
setdiff(ss1, ss2)
```

The two arguments are sorted sets with the same key and order type. This operation computes the difference, i.e., a sorted set containing entries that in are in `ss1` but not `ss2`. Time: O(*cn* log *n*), where *n* is the total size of the two containers.
