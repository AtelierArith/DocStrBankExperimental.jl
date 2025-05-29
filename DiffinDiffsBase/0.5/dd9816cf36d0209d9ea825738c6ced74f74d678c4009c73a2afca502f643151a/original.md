```
apply(d, by::Pair)
```

Apply a function elementwise to the specified column(s) in a `Tables.jl`-compatible table `d` and return the result.

Depending on the argument(s) accepted by a function `f`, it is specified with argument `by` as either `column_index => f` or `column_indices => f` where `column_index` is either a `Symbol` or `Int` for a column in `d` and `column_indices` is an iterable collection of such indices for multiple columns. `f` is applied elementwise to each specified column to obtain an array of returned values.
