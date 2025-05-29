```
groupby2_dict_indices(xs; keyfunc=identity, compare=isequal)
```

An iterator that yields a pair `(k,ig)` of a key and corresponding group of indices from the iterator `xs`, where the key `k` is computed by applying `keyfunc` to each element of `xs`. Compare adjacent keys by `compare` function, then, emits the key `k` and the vector `ig` of the group of indices.

See [documentation](https://hsugawa8651.github.io/GroupNumbers.jl/)
