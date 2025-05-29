```
intersect(ss, others...)
```

Each argument is a SortedSet with the same key and order type. The return variable is a new SortedSet that is the intersection of all the sets that are input. Time: O(*cn* log *n*), where *n* is the total number of items in all the arguments.
