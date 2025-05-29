```
insert!(sc, k)
```

Argument `sc` is a SortedDict or SortedMultiDict, `k` is a key and `v` is the corresponding value. This inserts the `(k,v)` pair into the container. If the key is already present in a SortedDict, this overwrites the old value. In the case of SortedMultiDict, no overwriting takes place (since SortedMultiDict allows the same key to associate with multiple values). In the case of SortedDict, the return value is a pair whose first entry is boolean and indicates whether the insertion was new (i.e., the key was not previously present) and the second entry is the semitoken of the new entry. In the case of SortedMultiDict, a semitoken is returned (but no boolean). Time: O(*c* log *n*)
