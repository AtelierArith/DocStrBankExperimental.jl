```
merge!(sc, sc1...)
```

This updates `sc` by merging SortedDicts or SortedMultiDicts `sc1`, etc. into `sc`. These must all must have the same key-value types. In the case of keys duplicated among the arguments, the rightmost argument that owns the key gets its value stored for SortedDict. In the case of SortedMultiDict all the key-value pairs are stored, and for overlapping keys the ordering is left-to-right. This function is not available for SortedSet, but the `union!` function (see below) provides equivalent functionality. Time: O(*cN* log *N*), where *N* is the total size of all the arguments.
