```
import_bibtex(input; check = :error)
```

Import a BibTeX file or parse a BibTeX string and convert it to the internal bibliography format. The `check` keyword argument can be set to `:none` (or `nothing`), `:warn`, or `:error` to raise appropriate logs.
