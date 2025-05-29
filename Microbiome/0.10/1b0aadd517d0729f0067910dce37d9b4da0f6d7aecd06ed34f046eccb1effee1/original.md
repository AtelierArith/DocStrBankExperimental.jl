```
featuretotals(at::AbstractAbundanceTable)
```

Returns sum of each row (feature) in `at`. Note, return value is a nfeatures x 1 `Matrix`, not a `Vector`. If you need 1D `Vector`, use `vec(featuretotals(at))`.
