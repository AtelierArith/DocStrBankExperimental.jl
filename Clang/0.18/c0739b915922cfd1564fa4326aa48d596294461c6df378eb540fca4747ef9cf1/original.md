```
parse_headers(
    index::Index,
    headers::Vector{String},
    args::Vector{String}=[],
    flags=CXTranslationUnit_None,
) -> Vector{TranslationUnit}
```

Return a [`TranslationUnit`](@ref) vector for the given headers.

See also [`parse_header`](@ref).
