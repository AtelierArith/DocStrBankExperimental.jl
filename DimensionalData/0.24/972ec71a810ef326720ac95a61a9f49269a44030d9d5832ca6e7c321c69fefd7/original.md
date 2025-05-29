```
label(x) => String
label(x, dims::Tuple) => NTuple{N,String}
label(x, dim) => String
label(xs::Tuple) => NTuple{N,String}
```

Get a plot label for data or a dimension. This will include the name and units if they exist, and anything else that should be shown on a plot.

Second argument `dims` can be `Dimension`s, `Dimension` types, or `Symbols` for `Dim{Symbol}`.
