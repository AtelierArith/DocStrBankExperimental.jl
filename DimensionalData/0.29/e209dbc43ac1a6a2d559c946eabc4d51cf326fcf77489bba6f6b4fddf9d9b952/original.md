```
metadata(x) => (object metadata)
metadata(x, dims::Tuple)  => Tuple (Dimension metadata)
metadata(xs::Tuple) => Tuple
```

Returns the metadata for an object or for the specified dimension(s)

Second argument `dims` can be `Dimension`s, `Dimension` types, or `Symbols` for `Dim{Symbol}`.
