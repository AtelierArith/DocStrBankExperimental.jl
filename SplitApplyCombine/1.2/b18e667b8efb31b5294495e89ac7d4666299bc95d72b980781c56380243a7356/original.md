```
groupreduce(by, f, op, iter...; [init])
```

Applies a `mapreduce`-like operation on the groupings labeled by passing the elements of `iter` through `by`. Mostly equivalent to `map(g -> reduce(op, g), group(by, f, iter))`, but designed to be more efficient. If multiple collections (of the same length) are provided, the transformations `by` and `f` occur elementwise.
