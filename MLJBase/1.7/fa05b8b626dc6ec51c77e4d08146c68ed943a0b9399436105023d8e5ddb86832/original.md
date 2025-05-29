```
selectrows(X::AbstractNode, r)
```

Returns a `Node` object `N` such that `N() = selectrows(X(), r)` (and `N(rows=s) = selectrows(X(rows=s), r)`).
