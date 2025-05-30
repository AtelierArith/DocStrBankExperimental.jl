```julia
contenttype_from_mime(mime::MIME)::String
```

MIMEをContent-Typeヘッダー値に変換します。これには`charset`パラメータが含まれる場合があります。

# 例:

```julia
contenttype_from_mime(MIME"application/json"()) == "application/json; charset=utf-8"
contenttype_from_mime(MIME"application/x-bogus"()) == "application/x-bogus"
contenttype_from_mime(mime_from_extension(".png", MIME"application/octet-stream"())) == "image/png"
```

# 参照:

[`charset_from_mime`](@ref), [`mime_from_contenttype`](@ref)
