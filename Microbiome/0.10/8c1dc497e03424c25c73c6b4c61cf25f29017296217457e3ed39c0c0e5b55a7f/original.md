```
sampletotals(at::AbstractAbundanceTable)
```

Returns sum of each row (feature) in `at`. Note, return value is a 1 x nsamples `Matrix`, not a `Vector`. If you need 1D `Vector`, use `vec(sampletotals(at))`.
