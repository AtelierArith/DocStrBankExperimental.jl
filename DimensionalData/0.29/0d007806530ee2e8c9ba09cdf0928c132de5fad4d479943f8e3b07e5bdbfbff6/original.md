```
hasselection(x, selector) => Bool
hasselection(x, selectors::Tuple) => Bool
```

Check if indexing into x with `selectors` can be performed, where x is some object with a `dims` method, and `selectors` is a `Selector` or `Dimension` or a tuple of either.
