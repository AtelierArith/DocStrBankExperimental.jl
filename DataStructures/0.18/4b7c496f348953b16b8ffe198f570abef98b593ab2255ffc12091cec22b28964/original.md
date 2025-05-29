```
setdiff!(ss, iterable)
```

This function deletes items in `ss` that appear in the second argument. The second argument must be iterable and its entries must be convertible to the key type of m1. Time: O(*cm* log *n*), where *n* is the size of `ss` and *m* is the number of items in `iterable`.
