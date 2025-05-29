```
fileexts_from_mime(mime::Union{Symbol,AbstractString,MIME}) -> fileexts::Vector{Symbol}
```

List file extentions `fileexts` known to be used for `mime`.  Return an empty tuple if not found.

# Example

```jldoctest
julia> using MIMEFileExtensions

julia> fileexts_from_mime("image/jpeg")
3-element Vector{Symbol}:
 :jpeg
 :jpg
 :jpe

julia> fileexts_from_mime(MIME"image/png"())
1-element Vector{Symbol}:
 :png
```
