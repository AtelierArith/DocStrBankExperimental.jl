```
weights(g::AbstractValGraph[, key]; zerovalue)
```

Return a matrix where entry (i,j) is the value of the edge `i -- j` for the specific `key` in `g`.

If `g` has no edge values, `key` should be omitted and `DefaultDistance(g)` is returned. Otherwise the result is a `ValMatrix`. If `g` has a single value per edge, `key` can be omitted. If the optional argument `zerovalue` is specified, then this value will be used if entry (i, j) is not an edge in `g`. `zerovalue` cannot be used for graphs without any edge values.
