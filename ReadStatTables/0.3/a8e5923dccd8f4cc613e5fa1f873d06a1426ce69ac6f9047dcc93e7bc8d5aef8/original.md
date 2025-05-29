```
ReadStatTable(table::ReadStatTable, ext::AbstractString; kwargs...)
```

Construct a `ReadStatTable` from an existing `ReadStatTable` for a supported file format with extension `ext`.

# Keywords

  * `update_width::Bool = true`: determine the storage width for each string variable by checking the actual data columns instead of any existing metadata value.
