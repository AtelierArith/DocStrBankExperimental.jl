```
FlexTable(name1 = array1, ...)
```

Create a column-storage-based `FlexTable` with column names `name1`, etc, from arrays `array1`, etc. The input arrays `array1`, etc, must share the same dimensionality and indices.

`FlexTable` itself is an `AbstractArray` whose elements are `NamedTuple`s of the form `(name1 = first(array1), ...)`, etc. Rows of the table are obtained via standard array indexing `table[i]`, and columns via `table.name`.

`FlexTable` differs from `Table` in that the columns are mutable - you may add, remove, rename and replace entire columns of a `FlexTable`, but not a `Table`. However, `Table` can access and iterate rows in local scope with fast, fully type-inferred code while `FlexTable` will be more efficient with a higher-order interface.
