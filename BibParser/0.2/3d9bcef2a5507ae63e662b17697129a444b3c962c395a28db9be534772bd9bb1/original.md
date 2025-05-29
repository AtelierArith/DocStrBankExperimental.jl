```
parse_file(path::String, parser::Symbol = :BibTeX; check=:error)
```

Parse a bibliography file. Default to BibTeX format. Other options available: CFF (CSL-JSON coming soon). For bibliography formats with formatting rules (such as `:BibTeX`), the `check` keyword argument can be set to `:none` (or `nothing`), `:warn`, or `:error`.
