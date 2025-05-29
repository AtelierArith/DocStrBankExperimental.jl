```
sp(i, j:k, ...)
sp(pattern)
```

The first form with integer and integer range arguments is a pattern selecting by the id number in the Suite Sparse collection.

The second form is a pattern, which selects a matrix in the Suite Sparse collection, which corresponds to the pattern by name, even if the name is from the Matrix Market collection.

example:     mdlist(sp("*/*/1138*bus")) == ["HB/1138*bus"]
