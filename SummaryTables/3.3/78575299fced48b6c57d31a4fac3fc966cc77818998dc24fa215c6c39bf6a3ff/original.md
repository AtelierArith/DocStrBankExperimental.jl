```
listingtable(table, variable, [pagination];
    rows = [],
    cols = [],
    summarize_rows = [],
    summarize_cols = [],
    variable_header = true,
    table_kwargs...
)
```

Create a listing table `Table` from `table` which displays raw values from column `variable`.

## Arguments

  * `table`: Data source which must be convertible to a `DataFrames.DataFrame`.
  * `variable`: Determines which variable's raw values are shown. Can either be a `Symbol` or `String` such as `:ColumnA`, or alternatively a `Pair` where the second element is the display name, such as `:ColumnA => "Column A"`.
  * `pagination::Pagination`: If a pagination object is passed, the return type changes to `PaginatedTable`. The `Pagination` object may be created with keywords `rows` and/or `cols`. These must be set to `Int`s that determine how many group sections along each side are included in one page. These group sections are determined by the summary structure, because pagination never splits a listing table within rows or columns that are being summarized together. If `summarize_rows` or `summarize_cols` is empty or unset, each group along that side is its own section. If `summarize_rows` or `summarize_cols` has a group passed via the `column => ...` syntax, the group sections along that side are determined by `column`. If no such `column` is passed (i.e., the summary along that side applies to the all groups) there is only one section along that side, which means that this side cannot be paginated into more than one page.

## Keyword arguments

  * `rows = []`: Grouping structure along the rows. Should be a `Vector` where each element is a grouping variable, specified as a `Symbol` or `String` such as `:Column1`, or a `Pair`, where the first element is the symbol and the second a display name, such as `:Column1 => "Column 1"`. Specifying multiple grouping variables creates nested groups, with the last variable changing the fastest.
  * `cols = []`: Grouping structure along the columns. Follows the same structure as `rows`.
  * `summarize_rows = []`: Specifies functions to summarize `variable` with along the rows. Should be a `Vector`, where each entry is one separate summary. Each summary can be given as a `Function` such as `mean` or `maximum`, in which case the display name is the function's name. Alternatively, a display name can be given using the pair syntax, such as `mean => "Average"`. By default, one summary is computed over all groups. You can also pass `name => [...]` where name, either a `Symbol` or `String`, is a grouping column, to compute one summary for each level of that group.
  * `summarize_cols = []`: Specifies functions to summarize `variable` with along the columns. Follows the same structure as `summarize_rows`.
  * `variable_header = true`: Controls if the cell with the name of the summarized `variable` is shown.
  * `sort = true`: Sort the input table before grouping. Pre-sort as desired and set to `false` when you want to maintain a specific group order or are using non-sortable objects as group keys.

All other keywords are forwarded to the `Table` constructor, refer to its docstring for details.

## Example

```
using Statistics

tbl = [
    :Apples => [1, 2, 3, 4, 5, 6, 7, 8],
    :Batch => [1, 1, 1, 1, 2, 2, 2, 2],
    :Checked => [true, false, true, false, true, false, true, false],
    :Delivery => ['a', 'a', 'b', 'b', 'a', 'a', 'b', 'b'],
]

listingtable(
    tbl,
    :Apples => "Number of apples",
    rows = [:Batch, :Checked => "Checked for spots"],
    cols = [:Delivery],
    summarize_cols = [sum => "total"],
    summarize_rows = :Batch => [mean => "average", sum]
)
```
