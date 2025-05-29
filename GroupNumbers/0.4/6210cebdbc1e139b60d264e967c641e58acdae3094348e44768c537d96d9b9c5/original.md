```
groupby_numbers_dict(xs; keyfunc=identity, emit=identity, kwargs)
```

An iterator that yields a pair `(k,xg)` of a key and corresponding group of elements from the iterator `xs` of presumably numbers, where the key `k` is computed by applying `keyfunc` to each element of `xs`. Compare adjacent keys by `isapprox` function with supplied `kwargs` optional parameters,  then, emits the key `k` and the vector `xg` of group of elements.

See [documentation](https://hsugawa8651.github.io/GroupNumbers.jl/)
