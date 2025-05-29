```
groupby_numbers(xs; keyfunc=identity, emit=identity, kwargs)
```

An iterator that yields a group `xg` of numbers from the iterator `xs` of presumably numbers, where the key is computed by applying `keyfunc` to each element of `xs`. Compare adjacent keys by `isapprox` function with supplied `kwargs` optional parameters,  then, emit the vector `xg` of the group of numbers.

See [documentation](https://hsugawa8651.github.io/GroupNumbers.jl/)
