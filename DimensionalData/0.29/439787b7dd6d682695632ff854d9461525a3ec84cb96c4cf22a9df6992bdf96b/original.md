```
name(x) => Symbol
name(xs:Tuple) => NTuple{N,Symbol}
name(x, dims::Tuple) => NTuple{N,Symbol}
name(x, dim) => Symbol
```

Get the name of an array or Dimension, or a tuple of of either as a Symbol.

Second argument `dims` can be `Dimension`s, `Dimension` types, or `Symbols` for `Dim{Symbol}`.
