```
expand(data, column_defs=nothing;
        default_value = missing,
        lazy_columns::Bool = false,
        pool_arrays::Bool = false,
        column_names::Dict = Dict{Tuple, Symbol}(),
        column_style::Symbol=:flat,
        name_join_pattern = "_")
```

Expand a nested data structure into a Tables

## Args:

  * `data::Any` - The nested data to unpack
  * `column_defs::Vector{ColumnDefinition}` - A list of paths to follow in `data`, ignoring other branches. Optional. Default: `nothing`.

## Kwargs:

  * `lazy_columns::Bool` - If true, return columns using a lazy iterator. If false, `collect` into regular vectors before returning. Default: `true` (don't collect).
  * `pool_arrays::Bool` - If true, use pool arrays to `collect` the columns. Default: `false`.
  * `column_names::Dict{Tuple, Symbol}` - A lookup to replace column names in the final result with any other symbol
  * `column_style::Symbol` - Choose returned column style from `:nested` or `:flat`. If nested, `column_names` are ignored   and a TypedTables.Table is returned in which the columns are nested in the same structure as the source data. Default: `:flat`
  * `name_join_pattern::String` - A pattern to put between the keys when joining the path into a column name. Default: `"_"`.

## Returns

`::NamedTuple` when `column_style = :flat` or `TypedTable.Table` when `column_style = :nested`.
