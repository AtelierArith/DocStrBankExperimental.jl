```
render_alphanumeric_range(template::AbstractString) :: String
```

Generate a string containing a number from a *numeric range* template. Such numeric templates may contain options separated by a `';'` caracter. Additionally, options can assume a single template format (e.g. `"4##"`) or specify a range using the `':'` character inside the option (e.g. `"2##:3##"` specifies numbers between 200 and 399).

# Example

```@repl
julia> render_alphanumeric_range("4#####")
"412345"

julia> render_alphanumeric_range("34####;37####")  # selects 34#### or 37####
"349790"

julia> render_alphanumeric_range("51####:55####")
"532489"

julia> render_alphanumeric_range("2221##:2720##;51####:55####")  # selects 2221##:2720## or 51####:55####
"250000"
```
