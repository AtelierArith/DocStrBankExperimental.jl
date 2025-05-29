```
partitions(s::AbstractVector)
```

Generate all set partitions of the elements of an array `s`, represented as arrays of arrays. Because the number of partitions can be very large, this function returns an iterator object. Use `collect(partitions(s))` to get an array of all partitions. The number of partitions to generate can be efficiently computed using `length(partitions(s))`.
