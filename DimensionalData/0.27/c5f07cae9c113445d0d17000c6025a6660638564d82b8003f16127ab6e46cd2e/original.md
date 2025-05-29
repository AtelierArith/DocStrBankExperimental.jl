```
dims(x, [dims::Tuple]) => Tuple{Vararg{Dimension}}
dims(x, dim) => Dimension
```

Return a tuple of `Dimension`s for an object, in the order that matches the axes or columns of the underlying data.

`dims` can be `Dimension`, `Dimension` types, or `Symbols` for `Dim{Symbol}`.

The default is to return `nothing`.
