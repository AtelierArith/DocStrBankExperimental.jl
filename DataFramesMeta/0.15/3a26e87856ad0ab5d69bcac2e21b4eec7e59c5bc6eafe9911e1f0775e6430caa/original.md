```
@note!(df, args...)
```

Assign notes to columns in a data frame using `:col = note` syntax. Shorthand for `note!(df, col, note)` from TablesMetadataTools.jl.

Use `@note!` for longer explanations of columns. Use `@label!` for short descriptions, primarily for pretty printing.

Returns `df`, with the notes of `df` modified.

```julia-repl

julia> df = DataFrame(wage = 12);

julia> @note! df :wage = "
       Wage per hour in 2014 USD taken from ACS data provided by IPUMS.

       Wage per hour is measured directly for hourly workers. For
       salaried workers, equal to salary / hours worked.
       ";

julia> printnotes(df)
Column: wage
────────────

Wage per hour in 2014 USD taken from ACS data provided by IPUMS.

Wage per hour is measured directly for hourly workers. For
salaried workers, equal to salary / hours worked.



julia> @note! df :wage = "Wage is capped at 99th percentile";

julia> printnotes(df)
Column: wage
────────────

Wage per hour in 2014 USD taken from ACS data provided by IPUMS.

Wage per hour is measured directly for hourly workers. For
salaried workers, equal to salary / hours worked.

Wage is capped at 99th percentile
```
