```
union!(ss, iterable)
```

This function inserts each item from the second argument (which must iterable) into the SortedSet `ss`. The items must be convertible to the key-type of `ss`. Time: O(*ci* log *n*) where *i* is the number of items in the iterable argument.
