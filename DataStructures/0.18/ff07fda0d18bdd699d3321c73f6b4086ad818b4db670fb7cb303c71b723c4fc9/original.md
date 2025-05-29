```
last(sc)
```

Argument `sc` is a SortedDict, SortedMultiDict or SortedSet. This function returns the last item (a `k=>v` pair for SortedDict and SortedMultiDict or a key for SortedSet) according to the sorted order in the container. Thus, `last(sc)` is equivalent to `deref((sc,lastindex(sc)))`. It is an error to call this function on an empty container. Time: O(log *n*)
