```
groupby2_dict(xs; keyfunc=identity, compare=isequal, emit=identity)
```

An iterator that yields a pair `(k,xg)` of key and corresponding group of elements from the iterator `xs`, where the key `k` is computed by applying `keyfunc` to each element of `xs`. Compare adjacent keys by `compare` function, then, emits the key `k` and the vector `xg` of the group of elements.

See [documentation](https://hsugawa8651.github.io/GroupNumbers.jl/)
