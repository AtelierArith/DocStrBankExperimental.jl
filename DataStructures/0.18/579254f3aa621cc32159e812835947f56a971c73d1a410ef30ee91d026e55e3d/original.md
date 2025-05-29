```
union(ss, iterable...)
```

This function creates a new SortedSet (the return argument) and inserts each item from `ss` and each item from each iterable argument into the returned SortedSet. Time: O(*cn* log *n*) where *n* is the total number of items in all the arguments.
