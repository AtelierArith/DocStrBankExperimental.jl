```
partitions(s::AbstractVector, m::Int)
```

Generate all set partitions of the elements of an array `s` into exactly `m` subsets, represented as arrays of arrays. Because the number of partitions can be very large, this function returns an iterator object. Use `collect(partitions(s, m))` to get an array of all partitions. The number of partitions into `m` subsets is equal to the Stirling number of the second kind, and can be efficiently computed using `length(partitions(s, m))`.
