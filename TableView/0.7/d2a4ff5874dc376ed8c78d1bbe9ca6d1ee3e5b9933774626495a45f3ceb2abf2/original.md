```
showtable(table; options::Dict{Symbol, Any} = Dict{Symbol, Any}(), option_mutator! = identity,
          dark = false, height = :auto, width = "100%", cell_changed = nothing)
```

Return a `WebIO.Scope` that displays the provided `table`.

Optional arguments:

  * `options`: Directly passed to agGrid's `Grid` constructor. Refer to the [documentation](https://www.ag-grid.com/documentation/) for more info.
  * `options_mutator!`: Runs on the `options` dictionary populated by TableView and allows for customizing the grid (at your own risk – you can break the package by supplying invalid options).
  * `dark`: Switch to a dark theme.
  * `title`: Displayed above the table if non-empty;
  * `height`/`width`: CSS attributes specifying the output height and with.
  * `cell_changed`: Either `nothing` or a function that takes a single argument with the fields `"new"`, `"old"`, `"row"`, and `"col"`. This function is called whenever the user edits a table field. Note that all values will be strings, so you need to do the necessary conversions yourself.
