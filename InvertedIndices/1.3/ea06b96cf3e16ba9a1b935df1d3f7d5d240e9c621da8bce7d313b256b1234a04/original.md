```
InvertedIndex(idx)
Not(idx)
```

Construct an inverted index, selecting all indices not in the passed `idx`.

Upon indexing into an array, the `InvertedIndex` behaves like a 1-dimensional collection of the indices of the array that are not in `idx`. Bounds are checked to ensure that all indices in `idx` are within the bounds of the array — even though they are skipped. The `InvertedIndex` behaves like a 1-dimensional collection of its inverted indices. If `idx` spans multiple dimensions (like a multidimensional logical mask or `CartesianIndex`), then the inverted index will similarly span multiple dimensions.

When indexing into a `NamedTuple`, the `InvertedIndex` can wrap either a `Symbol`, a vector of `Symbol`s, or a tuple of `Symbol`s and selects the fields of the `NamedTuple` that are not in `idx`.
