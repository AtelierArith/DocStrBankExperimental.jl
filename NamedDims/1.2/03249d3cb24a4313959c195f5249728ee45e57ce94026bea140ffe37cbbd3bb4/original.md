```
refine_names(x, names)
```

Refine the names of the dimensions of `x` to match `names`. This is like [`rename`](ref), but it only affects unnamed dimensions. I.e. dimensions of a `NamedDimsArray` called `:_`, or any dimensions of an `AbstractArray` in general.
