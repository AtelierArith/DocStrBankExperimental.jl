```
compcode(s::AbstractString)
```

Return a nonnegative integer code used internally by Blosc to identify the compressor. Throws an `ArgumentError` if `s` is not the name of a supported algorithm.
