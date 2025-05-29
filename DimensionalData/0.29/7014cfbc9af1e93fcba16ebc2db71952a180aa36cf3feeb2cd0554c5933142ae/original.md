```
refdims(x, [dims::Tuple]) => Tuple{Vararg{Dimension}}
refdims(x, dim) => Dimension
```

Reference dimensions for an array that is a slice or view of another array with more dimensions.

`slicedims(a, dims)` returns a tuple containing the current new dimensions and the new reference dimensions. Refdims can be stored in a field or discarded, as it is mostly to give context to plots. Ignoring refdims will simply leave some captions empty.

The default is to return an empty `Tuple` `()`.
