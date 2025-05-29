```
summarytable(table, variable;
    rows = [],
    cols = [],
    summary = [],
    variable_header = true,
    celltable_kws...
)
```

Create a summary table `Table` from `table`, which summarizes values from column `variable`.

## Arguments

  * `table`: Data source which must be convertible to a `DataFrames.DataFrame`.
  * `variable`: Determines which variable from `table` is summarized. Can either be a `Symbol` or `String` such as `:ColumnA`, or alternatively a `Pair` where the second element is the display name, such as `:ColumnA => "Column A"`.

## Keyword arguments

  * `rows = []`: Grouping structure along the rows. Should be a `Vector` where each element is a grouping variable, specified as a `Symbol` or `String` such as `:Column1`, or a `Pair`, where the first element is the symbol and the second a display name, such as `:Column1 => "Column 1"`. Specifying multiple grouping variables creates nested groups, with the last variable changing the fastest.
  * `cols = []`: Grouping structure along the columns. Follows the same structure as `rows`.
  * `summary = []`: Specifies functions to summarize `variable` with. Should be a `Vector`, where each entry is one separate summary. Each summary can be given as a `Function` such as `mean` or `maximum`, in which case the display name is the function's name. Alternatively, a display name can be given using the pair syntax, such as `mean => "Average"`. By default, one summary is computed over all groups. You can also pass `name => [...]` where name, either a `Symbol` or `String`, is a grouping column, to compute one summary for each level of that group.
  * `variable_header = true`: Controls if the cell with the name of the summarized `variable` is shown.
  * `sort = true`: Sort the input table before grouping. Pre-sort as desired and set to `false` when you want to maintain a specific group order or are using non-sortable objects as group keys.

All other keywords are forwarded to the `Table` constructor, refer to its docstring for details.

## Example

```
using Statistics

tbl = [
    :Apples => [1, 2, 3, 4, 5, 6, 7, 8],
    :Batch => [1, 1, 1, 1, 2, 2, 2, 2],
    :Delivery => ['a', 'a', 'b', 'b', 'a', 'a', 'b', 'b'],
]

summarytable(
    tbl,
    :Apples => "Number of apples",
    rows = [:Batch],
    cols = [:Delivery],
    summary = [length => "N", mean => "average", sum]
)
```
