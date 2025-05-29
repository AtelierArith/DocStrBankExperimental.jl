```
lowrank_stream(k, d, n, ν = 0.0; out_dic = nothing)
```

Returns a `RandomStreamDataset` which returns `n` `d`-dimensional vectors lying in a `k`-dimensional subspace. This stream can be iterated over using a `BatchIterator` wrapper.
