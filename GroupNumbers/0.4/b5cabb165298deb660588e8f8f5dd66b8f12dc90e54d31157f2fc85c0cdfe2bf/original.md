```
groupby_numbers_indices(xs; keyfunc=identity, kwargs)
```

An iterator that yields a group `ig` of indices from the iterator `xs` of presumably numbers, where the key is computed by applying `keyfunc` to each element of `xs`. Compare adjacent keys by `isapprox` function with supplied `kwargs` optional parameters,  then, emits the vector `ig` of the group of indices.

See [documentation](https://hsugawa8651.github.io/GroupNumbers.jl/)
