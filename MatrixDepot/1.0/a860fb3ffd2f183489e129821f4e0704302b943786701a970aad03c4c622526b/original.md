```
@pred(expression)
```

Generate a predicate function using the expression as function body. Variable names within the expression, which are properties of `RemoteMatrixData` (e.g. `title`, `m`, `nnz`) are used to access `data.title` etc. Other variable names, are used from the outer scope.

example: `maxnnz = 1_000; listnames(@pred(n <= maxnnz))` would produce a list of all data with less than `maxnnz` structural non-zeros.
