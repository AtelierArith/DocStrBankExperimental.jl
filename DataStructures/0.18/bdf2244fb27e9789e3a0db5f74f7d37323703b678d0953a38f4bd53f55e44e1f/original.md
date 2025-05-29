```
insert!(sc, k)
```

Argument `sc` is a SortedSet and `k` is a key. This inserts the key into the container. If the key is already present, this overwrites the old value. (This is not necessarily a no-op; see below for remarks about the customizing the sort order.) The return value is a pair whose first entry is boolean and indicates whether the insertion was new (i.e., the key was not previously present) and the second entry is the semitoken of the new entry. Time: O(*c* log *n*)
