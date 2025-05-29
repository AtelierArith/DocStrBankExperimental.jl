```
table_one(table, analyses; keywords...)
```

Construct a "Table 1" which summarises the patient baseline characteristics from the provided `table` dataset. This table is commonly used in biomedical research papers.

It can handle both continuous and categorical columns in `table` and summary statistics and hypothesis testing are able to be customised by the user. Tables can be stratified by one, or more, variables using the `groupby` keyword.

## Keywords

  * `groupby`: Which columns to stratify the dataset with, as a `Vector{Symbol}`.
  * `nonnormal`: A vector of column names where hypothesis tests for the `:nonnormal` type are chosen.
  * `minmax`: A vector of column names where hypothesis tests for the `:minmax` type are chosen.
  * `tests`: A `NamedTuple` of hypothesis test types to use for `categorical`, `nonnormal`, `minmax`, and `normal` variables.
  * `combine`: An object from `MultipleTesting` to use when combining p-values.
  * `show_total`: Display the total column summary. Default is `true`.
  * `group_totals`: A group `Symbol` or `String` or vector of symbols/strings specifying for which group levels totals should be added. Any group levels but the topmost can be chosen (the topmost being already handled by the `show_total` option). Default is `Symbol[]`.
  * `total_name`: The name for all total columns. Default is `"Total"`.
  * `show_n`: Display the number of rows for each group key next to its label.
  * `show_pvalues`: Display the `P-Value` column. Default is `false`.
  * `show_testnames`: Display the `Test` column. Default is `false`.
  * `show_confints`: Display the `CI` column. Default is `false`.
  * `sort`: Sort the input table before grouping. Default is `true`. Pre-sort as desired and set to `false` when you want to maintain a specific group order or are using non-sortable objects as group keys.

## Deprecated keywords

  * `show_overall`: Use `show_total` instead

All other keywords are forwarded to the `Table` constructor, refer to its docstring for details.
