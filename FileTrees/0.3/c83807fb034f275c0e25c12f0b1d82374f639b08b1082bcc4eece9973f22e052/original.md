```
exec(x)
```

If `x` is a `FileTree`, computes any uncomputed `Thunk`s stored as values in it. Returns a new tree with the computed values. If `x` is a `File`, computes the value if it is a `Thunk`. Returns a new `File` with the computed value. If `x` is a `Thunk` (such as the result of a `reducevalues`), then exec will compute the result. If `x` is anything else, `exec` just returns the same value.
