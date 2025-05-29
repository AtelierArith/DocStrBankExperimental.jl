```
grid(items; ...)
grid(items...; ...)
```

Create a [`GridBox`](@ref) from the given items.

The `items` argument is one of:

  * A vector of other items. The top-level vector arranges its items in a column. Subsequent nesting of vectors switch between rows and columns, making it easy to create complex layouts.
  * A matrix, specifying two levels of nesting.
  * A `LayoutDOM` object, which is the terminal entry in the grid.
  * A [`Row`](@ref) or [`Column`](@ref), explicitly specifying a row or column of the grid.
  * `nothing`, representing a blank cell.

## Keyword arguments

  * `sizing_mode`: How the resulting grid is sized.
  * `nrows` or `ncols`: If `items` is a vector and one of these arguments is specified, it is partitioned into a 2D layout with the given number of rows or columns.
  * `item_width`, `item_height`: The width and height of each item.
  * `merge_tools=true`: When true, toolbars of constituent plots are merged into one.
  * `toolbar_location="above"`: Where to place the merged toolbar. May be `nothing`.
  * `toolbar_options`: A named tuple of options for the merged toolbar.
  * Remaining arguments are passed to [`GridBox`](@ref).
