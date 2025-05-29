```
Document(text::AbstractString, metadata::T; replacements=AUTOMATIC_REPLACEMENTS) where {T<:NamedTuple}
```

Represents a single string document. This object has two fields,

  * `text::String`
  * `metadata::T`

The `text` is automatically processed by applying the replacements from `replacements`, which defaults to [`AUTOMATIC_REPLACEMENTS`](@ref) and adding a space to the start and end of the document (if one doesn't exist already).
