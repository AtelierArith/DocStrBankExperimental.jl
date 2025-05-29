```
printlabels(df, [cols=All()]; unlabelled = true)
```

Pretty-print all labels in a data frame.

## Arguments

  * `cols`: Optional argument to select columns to print. Can be any valid multi-column selector, such as `Not(...)`, `Between(...)`, or a regular expression.
  * `unlabelled`: Keyword argument for whether to print the columns without user-defined labels. Deftaults to `true`. For column `col` without a user-defined label, `label(df, col)` returns the name of the column, `col`.

## Examples

```julia-repl
julia> df = DataFrame(wage = [12], age = [23]);

julia> @label! df :wage = "Hourly wage (2015 USD)";

julia> printlabels(df)
┌────────┬────────────────────────┐
│ Column │                  Label │
├────────┼────────────────────────┤
│   wage │ Hourly wage (2015 USD) │
│    age │                    age │
└────────┴────────────────────────┘

julia> printlabels(df, :wage)
┌────────┬────────────────────────┐
│ Column │                  Label │
├────────┼────────────────────────┤
│   wage │ Hourly wage (2015 USD) │
└────────┴────────────────────────┘

julia> printlabels(df; unlabelled = false)
┌────────┬────────────────────────┐
│ Column │                  Label │
├────────┼────────────────────────┤
│   wage │ Hourly wage (2015 USD) │
└────────┴────────────────────────┘

julia> printlabels(df, r"^wage")
┌────────┬────────────────────────┐
│ Column │                  Label │
├────────┼────────────────────────┤
│   wage │ Hourly wage (2015 USD) │
└────────┴────────────────────────┘
```
