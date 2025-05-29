```
groupby2_indices(xs; keyfunc=identity, compare=isequal)
```

An iterator that yields a group `ig` of indices from the iterator `xs`, where the key is computed by applying `keyfunc` to each element of `xs`. Compare adjacent keys by `compare` function, then, emits the vector `ig` of the group of indices.

See [documentation](https://hsugawa8651.github.io/GroupNumbers.jl/)
