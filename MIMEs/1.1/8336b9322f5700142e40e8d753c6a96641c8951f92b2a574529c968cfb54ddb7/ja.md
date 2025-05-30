```julia
compressible_from_mime(mime::MIME)::Bool
```

与えられたMIMEタイプのファイルがgzippedできるか/すべきか。

# 例:

```julia
compressible_from_mime(MIME"text/html"()) == true
compressible_from_mime(MIME"image/png"()) == false
compressible_from_mime(MIME"text/blablablaa"()) == false
```
