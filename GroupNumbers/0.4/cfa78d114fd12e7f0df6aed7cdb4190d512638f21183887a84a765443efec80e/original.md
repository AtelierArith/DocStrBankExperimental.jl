```
groupby2(xs; keyfunc=identity, compare=isequal, emit=identity)
```

An iterator that yields a group `xg` of elements from the iterator `xs`, where the key is computed by applying `keyfunc` to each element of `xs`. Compare adjacent keys by `compare` function, then, emits the vector `xg` of the group of elements.

See [documentation](https://hsugawa8651.github.io/GroupNumbers.jl/)
