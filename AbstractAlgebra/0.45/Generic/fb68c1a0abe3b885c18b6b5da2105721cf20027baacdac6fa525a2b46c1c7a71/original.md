```
partitionseq(lambda::Partition)
```

Return a sequence (as `BitVector`) of `false`s and `true`s constructed from `lambda`: tracing the lower contour of the Young Diagram associated to `lambda` from left to right a `true` is inserted for every horizontal and `false` for every vertical step. The sequence always starts with `true` and ends with `false`.
