```
 check_size(dims) -> len
```

checks the validity of the array size `dims` and yields the corresponding number of elements (throwing an `ArgumentError` exception if this is not the case). To be a valid array size, the values of `dims` must all be nonnegative.
