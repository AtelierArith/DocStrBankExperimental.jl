```
in(p, sc)
```

Returns true if `p` is in `sc`. In the case that `sc` is a SortedDict or SortedMultiDict, `p` is a key=>value pair. In the case that `sc` is a SortedSet, `p` should be a key. Time: O(*c* log *n* + *d*) for SortedDict and SortedSet, where *d* stands for the time to compare two values. In the case of SortedMultiDict, the time is O(*c* log *n* + *dl*), and *l* stands for the number of entries that have the key of the given pair. (So therefore this call is inefficient if the same key addresses a large number of values, and an alternative should be considered.)
