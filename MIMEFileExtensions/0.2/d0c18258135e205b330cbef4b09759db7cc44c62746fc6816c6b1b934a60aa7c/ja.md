```
fileexts_from_mime(mime::Union{Symbol,AbstractString,MIME}) -> fileexts::Vector{Symbol}
```

`mime` に対して知られているファイル拡張子 `fileexts` のリストを返します。見つからない場合は空のタプルを返します。

# 例

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
