```
high(X::LazySet)
```

Compute the highest coordinate of a set in each dimension.

### Input

  * `X` – set

### Output

A vector with the highest coordinate of the set in each dimension.

### Notes

See also `high(X::LazySet, i::Int)`.

The result is the uppermost corner of the box approximation, so it is not necessarily contained in `X`.
