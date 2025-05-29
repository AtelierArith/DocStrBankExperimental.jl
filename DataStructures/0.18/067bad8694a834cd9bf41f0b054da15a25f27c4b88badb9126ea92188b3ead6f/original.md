```
merge(sc1, sc2...)
```

This returns a SortedDict or SortedMultiDict that results from merging SortedDicts or SortedMultiDicts `sc1`, `sc2`, etc., which all must have the same key-value-ordering types. In the case of keys duplicated among the arguments, the rightmost argument that owns the key gets its value stored for SortedDict. In the case of SortedMultiDict all the key-value pairs are stored, and for keys shared between `sc1` and `sc2` the ordering is left-to-right. This function is not available for SortedSet, but the `union` function (see below) provides equivalent functionality. Time: O(*cN* log *N*), where *N* is the total size of all the arguments.
