```julia
extension_from_mime(mime::MIME[, default::T=""])::Union{String,T}
```

指定されたMIMEタイプのファイルに最も一般的に使用されるファイル拡張子を返します。

# 例:

```julia
extension_from_mime(MIME"application/json"()) == ".json"
extension_from_mime(MIME"text/html"()) == ".html"
extension_from_mime(MIME"text/blablablaa"()) == ""
extension_from_mime(MIME"text/blablablaa"(), ".bin") == ".bin"
```
