```
@label!(df, args...)
```

Assign labels to columns in a data frame using `:col = label` syntax. Shorthand for `label!(df, ...)` from TablesMetaDataTools.jl.

```julia-repl
julia> df = DataFrame(wage = 12);

julia> @label! df :wage = "Wage per hour (USD)";

julia> printlabels(df)
┌────────┬─────────────────────┐
│ Column │               Label │
├────────┼─────────────────────┤
│   wage │ Wage per hour (USD) │
└────────┴─────────────────────┘
```

Use `@label!` for short descriptions, primarily for pretty printing. Use `@note!` for longer explanations of columns.

Labels are "note"-style columnar metadata. Labels are preserved upon renaming and transformations. `@label! :x = "Lab"` over-writes any existing label for the column `:x`. To add information without overwriting, use [`@note!`](@ref).

Returns `df`, with the labels of `df` modified.

Like other DataFramesMeta.jl macros, `@label!` can be used in "keyword" format as well as block format.

```julia-repl
julia> df = DataFrame(wage = 12, tenure = 4);

julia> @label! df begin
           :wage = "Wage per hour (USD)"
           :tenure = "Tenure at job (months)"
       end;

julia> printlabels(df)
┌────────┬────────────────────────┐
│ Column │                  Label │
├────────┼────────────────────────┤
│   wage │    Wage per hour (USD) │
│ tenure │ Tenure at job (months) │
└────────┴────────────────────────┘
```
