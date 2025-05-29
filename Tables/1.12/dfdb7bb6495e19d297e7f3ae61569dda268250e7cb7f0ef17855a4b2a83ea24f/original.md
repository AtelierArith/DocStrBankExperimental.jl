```
Tables.columns(x) => AbstractColumns-compatible object
```

Accesses data of input table source `x` by returning an [`AbstractColumns`](@ref)-compatible object, which allows retrieving entire columns by name or index. A retrieved column is a 1-based indexable object that has a known length, i.e. supports `length(col)` and `col[i]` for any `i = 1:length(col)`. Note that even if the input table source is row-oriented by nature, an efficient generic definition of `Tables.columns` is defined in Tables.jl to build a `AbstractColumns`- compatible object object from the input rows.

The [`Tables.Schema`](@ref) of a `AbstractColumns` object can be queried via `Tables.schema(columns)`, which may return `nothing` if the schema is unknown. Column names can always be queried by calling `Tables.columnnames(columns)`, and individual columns can be accessed by calling `Tables.getcolumn(columns, i::Int )` or `Tables.getcolumn(columns, nm::Symbol)` with a column index or name, respectively.

Note that if `x` is an object in which columns are stored as vectors, the check that these vectors use 1-based indexing is not performed (it should be ensured when `x` is constructed).
