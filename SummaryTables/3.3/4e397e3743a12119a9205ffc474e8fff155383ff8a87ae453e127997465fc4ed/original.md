```
simple_table(table, [columns];
    halign = :center,
    subheaders = nothing,
    table_kwargs...
)
```

Create a simple `Table` displaying (a subset of) the raw columns from a `table`.

## Arguments

  * `table`: A Tables.jl compatible data source
  * `columns`: A vector of column names to select from the table, with optional display names attached. A column name can be either a `Symbol` or a `String`. A different display name can be passed in using the `Pair` syntax where the display name can be any object SummaryTables knows how to render, for example `[:a, :b => "B", "c"]`.

## Keyword arguments

  * `halign = :center`: Either `:left`, `:right`, `:center` or a vector of these values with as many entries as there are columns to display.
  * `subheaders = nothing`: To show subheaders, pass a vector of objects SummaryTables knows how to render, with as many entries as there are columns to display.
