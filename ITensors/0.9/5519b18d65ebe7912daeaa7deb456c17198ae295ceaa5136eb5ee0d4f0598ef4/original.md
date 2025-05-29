```
not(inds::Union{IndexSet, Tuple{Vararg{Index}}})
not(inds::Index...)
!(inds::Union{IndexSet, Tuple{Vararg{Index}}})
!(inds::Index...)
```

Represents the set of indices not in the specified IndexSet, for use in pattern matching (i.e. when searching for an index or priming/tagging specified indices).
