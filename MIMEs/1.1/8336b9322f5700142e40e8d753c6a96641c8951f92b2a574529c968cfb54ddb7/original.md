```julia
compressible_from_mime(mime::MIME)::Bool
```

Whether a file of the given MIME type can/should be gzipped.

# Examples:

```julia
compressible_from_mime(MIME"text/html"()) == true
compressible_from_mime(MIME"image/png"()) == false
compressible_from_mime(MIME"text/blablablaa"()) == false
```
