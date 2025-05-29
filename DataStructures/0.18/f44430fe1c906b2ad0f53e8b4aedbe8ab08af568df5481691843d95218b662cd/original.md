```
issubset(iterable, ss)
```

This function checks whether each item of the first argument is an element of the SortedSet `ss`. The entries must be convertible to the key-type of `ss`. Time: O(*cm* log *n*), where *n* is the sizes of `ss` and *m* is the number of items in `iterable`.
