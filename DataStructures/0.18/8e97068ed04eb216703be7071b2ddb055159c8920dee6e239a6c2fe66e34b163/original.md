```
delete!(sc, k)
```

Argument `sc` is a SortedDict or SortedSet and `k` is a key. This operation deletes the item whose key is `k`. It is a `KeyError` if `k` is not a key of an item in the container. After this operation is complete, any token addressing the deleted item is invalid. Returns `sc`. Time: O(*c* log *n*)
