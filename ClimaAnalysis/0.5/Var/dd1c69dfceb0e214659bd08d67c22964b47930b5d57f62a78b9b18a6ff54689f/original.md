```
permutedims(var::OutputVar, perm)
```

Permute the dimensions of `var` according to `perm`, an iterable of dimension names specifying the permutation.

The dimension names in `perm` does not need to be the same as the dimensions in `var`. For example, dimensions with names `lon` and `long` are identified as the longitude dimension.
