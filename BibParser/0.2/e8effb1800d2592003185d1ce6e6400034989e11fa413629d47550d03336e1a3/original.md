```
parse_entry(entry::String; parser::Symbol = :BibTeX, check = :error)
```

Parse a string entry. Default to BibTeX format. No other options available yet (CSL-JSON coming soon).

For bibliography formats with formatting rules (such as `:BibTeX`), the `check` keyword argument can be set to `:none` (or `nothing`), `:warn`, or `:error`.
