```
low(X::LazySet)
```

Compute the lowest coordinates of a set in each dimension.

### Input

  * `X` – set

### Output

A vector with the lowest coordinate of the set in each dimension.

### Notes

See also `low(X::LazySet, i::Int)`.

The result is the lowermost corner of the box approximation, so it is not necessarily contained in `X`.
