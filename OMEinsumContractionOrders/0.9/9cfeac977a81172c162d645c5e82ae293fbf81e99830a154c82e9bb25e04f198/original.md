```
label_elimination_order(code) -> Vector
```

Returns a vector of labels sorted by the order they are eliminated in the contraction tree. The contraction tree is specified by `code`, which e.g. can be a `NestedEinsum` instance.
