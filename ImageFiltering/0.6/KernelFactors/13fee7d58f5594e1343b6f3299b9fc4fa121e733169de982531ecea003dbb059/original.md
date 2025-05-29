```
kernelfactors(factors::Tuple)
```

Prepare a factored kernel for filtering. If passed a 2-tuple of vectors of lengths `m` and `n`, this will return a 2-tuple of `ReshapedVector`s that are effectively of sizes `m×1` and `1×n`. In general, each successive `factor` will be reshaped to extend along the corresponding dimension.

If passed a tuple of general arrays, it is assumed that each is shaped appropriately along its "leading" dimensions; the dimensionality of each is "extended" to `N = length(factors)`, appending 1s to the size as needed.
