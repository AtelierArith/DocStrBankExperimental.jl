```
DataFrameColumns{<:AbstractDataFrame}
```

A vector-like object that allows iteration over columns of an `AbstractDataFrame`.

Indexing into `DataFrameColumns` objects using integer, `Symbol` or string returns the corresponding column (without copying). Indexing into `DataFrameColumns` objects using a multiple column selector returns a subsetted `DataFrameColumns` object with a new parent containing only the selected columns (without copying).

`DataFrameColumns` supports most of the `AbstractVector` API. The key differences are that it is read-only and that the `keys` function returns a vector of `Symbol`s (and not integers as for normal vectors).

In particular `findnext`, `findprev`, `findfirst`, `findlast`, and `findall` functions are supported, and in `findnext` and `findprev` functions it is allowed to pass an integer, string, or `Symbol` as a reference index.
