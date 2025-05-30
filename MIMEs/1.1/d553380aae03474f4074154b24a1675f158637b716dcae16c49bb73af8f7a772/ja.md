```julia
charset_from_mime(mime::MIME[, default::T=nothing])::Union{String,T}
```

このタイプに関連付けられたデフォルトのcharsetがある場合、それを返します。知られていない場合、テキストMIMEはデフォルトで「UTF-8」となります。可能な値は：Union{Nothing, String}["UTF-8", "US-ASCII", "7-BIT", nothing]です。

# 例:

```julia
charset_from_mime(MIME"application/json"()) == "UTF-8"
charset_from_mime(MIME"application/x-bogus"()) == nothing
charset_from_mime(MIME"text/blablablaa"()) == "UTF-8" # これは `text/` mime であるため
charset_from_mime(MIME"text/blablablaa"(), "LATIN-1") == "LATIN-1"
```
