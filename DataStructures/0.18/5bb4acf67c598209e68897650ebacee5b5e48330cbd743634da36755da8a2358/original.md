```
packcopy(sc)
```

This returns a copy of `sc` in which the data is packed. When deletions take place, the previously allocated memory is not returned. This function can be used to reclaim memory after many deletions. Time: O(*cn* log *n*)
