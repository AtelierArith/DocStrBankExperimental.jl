```
parse_headers(
    index::Index,
    headers::Vector{String},
    args::Vector{String}=[],
    flags=CXTranslationUnit_None,
) -> Vector{TranslationUnit}
```

指定されたヘッダーのために [`TranslationUnit`](@ref) ベクターを返します。

[`parse_header`](@ref) も参照してください。
