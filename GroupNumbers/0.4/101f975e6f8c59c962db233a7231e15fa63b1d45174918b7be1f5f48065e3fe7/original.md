```
groupby_numbers_dict_indices(xs; keyfunc=identity, kwargs)
```

An iterator that yields a pair `(k,ig)` of a key and corresponding group of indices from the iterator `xs` of presumably numbers, where the key `k` is computed by applying `keyfunc` to each element of `xs`. Compare adjacent keys by `isapprox` function with supplied `kwargs` optional parameters,  then, emits the key `k` and the vector `ig` of the group of indices.

See [documentation](https://hsugawa8651.github.io/GroupNumbers.jl/)
