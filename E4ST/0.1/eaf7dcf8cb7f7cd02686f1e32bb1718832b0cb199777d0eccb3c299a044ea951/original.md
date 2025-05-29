```
summarize_table(s::Symbol) -> summary::DataFrame
```

Returns a summary of the table `s`.  Note that more information can be provided in the the `summary_table`, which contains a summary of all tables, including all information from `summarize_table`, plus additional columns specified.

See also [`get_table(data, name)`](@ref), [`read_summary_table!(config, data)`](@ref), [`get_table_summary(data, name)`](@ref)
