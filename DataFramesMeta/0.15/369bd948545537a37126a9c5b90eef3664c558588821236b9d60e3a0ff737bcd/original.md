```
printnotes(df, cols = All(); unnoted = false)
```

Print the notes and labels in a data frame.

## Arguments

  * `cols`: Optional argument to select columns to print. Can be any valid multi-column selector, such as `Not(...)`, `Between(...)`, or a regular expression.
  * `unnoted`: Keyword argument for whether to print the columns without user-defined notes or labels.

For the purposes of printing, column labels are printed in addition to notes. However column labels are not returned by `note(df, col)`.

```
julia> df = DataFrame(wage = [12], age = [23]);

julia> @label! df :age = "Age (years)";

julia> @note! df :wage = "Derived from American Community Survey";

julia> @note! df :wage = "Missing values imputed as 0 wage";

julia> @label! df :wage = "Hourly wage (2015 USD)";

julia> printnotes(df)
Column: wage
────────────
Label: Hourly wage (2015 USD)
Derived from American Community Survey
Missing values imputed as 0 wage

Column: age
───────────
Label: Age (years)
```
