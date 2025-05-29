```
search_variables(pattern::T, database::TelemetryDatabase = get_default_database()) where T<:Union{AbstractString, Regex} -> Nothing
```

Search for variables registered in `database` in which their label, alias, or description contains `pattern`. `pattern` can be a string or a regex.

!!! note
    If `pattern` is a string, the search will be case-insensitive.


!!! note
    If `database` is not provided, the default one is used.

