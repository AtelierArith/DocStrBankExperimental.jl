Tabular data with optional column names.

This corresponds to the part of tables between `{}`'s in PGFPlots, without the options or `table`, so that it can also be used for “inline” tables. [`Table`](@ref) will call the constructor for this type to convert arguments after `options`.

`data` is a matrix, which contains the contents of the table, which will be printed using `print_tex`. `colnames` is a vector of column names (converted to string), or `nothing` for a table with no column names.

When `rowsep` is `true`, an additional `\\` is used as a row separator. The default is `true`, this is recommended to avoid “fragility” issues with inline tables.

!!! note
    `Table` queries `TableData` for its `rowsep`, and adds the relevant option accordingly. When using “inline” tables, eg in options, you have to specify this manually for the container. See the gallery for examples.


After each index in `scanlines`, extra row separators are inserted. This can be used for skipping coordinates or implicitly defining the dimensions of a matrix for `surf` and `mesh` plots. They are expanded using [`expand_scanlines`](@ref).
