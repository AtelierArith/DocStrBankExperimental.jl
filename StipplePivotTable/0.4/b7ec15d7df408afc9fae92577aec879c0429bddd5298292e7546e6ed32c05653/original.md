```
pivottable(pt::PivotTable; columns::Union{Vector{Cell}, Nothing} = nothing,
           rows::Union{Vector{Cell}, Nothing} = nothing,
           values::Union{Vector{Value}, Nothing} = nothing,
           filters::Union{Vector{Filter}, Nothing} = nothing)
```

Create a pivot table from the given `PivotTable` object `pt`.

# Arguments

  * `pt::PivotTable`: The pivot table object containing the data.
  * `columns::Union{Vector{Cell}, Nothing}`: Optional. A vector of columns to include in the pivot table. Defaults to `columns(pt)` if not provided.
  * `rows::Union{Vector{Cell}, Nothing}`: Optional. A vector of rows to include in the pivot table. Defaults to `rows(pt)` if not provided.
  * `values::Union{Vector{Value}, Nothing}`: Optional. A vector of values to include in the pivot table. Defaults to `values(pt)` if not provided.
  * `filters::Union{Vector{Filter}, Nothing}`: Optional. A vector of filters to apply to the pivot table. Defaults to `filters(pt)` if not provided.

# Returns

  * A pivot table created using the specified columns, rows, values, and filters.
