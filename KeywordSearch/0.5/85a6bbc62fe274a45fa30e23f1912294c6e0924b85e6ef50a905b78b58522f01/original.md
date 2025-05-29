```
Query(text::AbstractString; replacements=AUTOMATIC_REPLACEMENTS) <: AbstractQuery
```

A query to search for an exact match of a string, with one field:

  * `text::String`

The `text` is automatically processed by applying the replacements from `replacements` (which defaults to [`AUTOMATIC_REPLACEMENTS`](@ref)).
