```julia
mime_from_contenttype(content_type::String[, default::T=nothing])::Union{MIME,T}
```

Content-Type ヘッダー値から MIME を抽出します。入力が空の場合、`default` が返されます。

# 例:

```julia
mime_from_contenttype("application/json; charset=utf-8") == MIME"application/json"()
mime_from_contenttype("application/x-bogus") == MIME"application/x-bogus"()
mime_from_contenttype("") == nothing
mime_from_contenttype("", MIME"application/octet-stream"()) == MIME"application/octet-stream"()
```

# 参照:

[`contenttype_from_mime`](@ref)
