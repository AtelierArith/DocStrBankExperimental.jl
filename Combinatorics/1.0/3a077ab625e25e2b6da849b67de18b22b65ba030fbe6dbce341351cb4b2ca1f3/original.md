```
partitions(n, m)
```

Generate all arrays of `m` integers that sum to `n`. Because the number of partitions can be very large, this function returns an iterator object. Use `collect(partitions(n, m))` to get an array of all partitions. The number of partitions to generate can be efficiently computed using `length(partitions(n, m))`.
