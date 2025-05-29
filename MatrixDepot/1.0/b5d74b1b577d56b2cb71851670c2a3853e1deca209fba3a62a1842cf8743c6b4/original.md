```
mm(i, j:k, ...)
mm(pattern)
```

The first form with integer and integer range arguments is a pattern selecting by the id number in the Matrix Market collection.

The second form is a pattern, which selects a matrix in the Matrix Market collection, which corresponds to the pattern by name, even if the name is from the Suite Sparse collection.

example:     mdlist(mm("*/1138*bus")) == ["Harwell-Boeing/psadmit/1138*bus"]
