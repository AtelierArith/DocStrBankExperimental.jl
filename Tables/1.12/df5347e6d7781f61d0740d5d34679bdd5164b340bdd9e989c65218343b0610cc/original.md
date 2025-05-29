```
Tables.rows(x) => Row iterator
```

Accesses data of input table source `x` row-by-row by returning an [`AbstractRow`](@ref)-compatible iterator. Note that even if the input table source is column-oriented by nature, an efficient generic definition of `Tables.rows` is defined in Tables.jl to return an iterator of row views into the columns of the input.

The [`Tables.Schema`](@ref) of an `AbstractRow` iterator can be queried via `Tables.schema(rows)`, which may return `nothing` if the schema is unknown. Column names can always be queried by calling `Tables.columnnames(row)` on an individual row, and row values can be accessed by calling `Tables.getcolumn(row, i::Int )` or `Tables.getcolumn(row, nm::Symbol)` with a column index or name, respectively.

See also [`rowtable`](@ref) and [`namedtupleiterator`](@ref).
