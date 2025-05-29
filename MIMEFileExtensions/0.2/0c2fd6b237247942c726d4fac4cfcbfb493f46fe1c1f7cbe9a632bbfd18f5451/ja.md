```
mimes_from_fileext(fileext::Union{Symbol,AbstractString}) -> mimes::Vector{Symbol}
```

ファイル拡張子 `fileext` に対して知られているMIME `mimes` のリストを返します。見つからない場合は空のタプルを返します。

# 例

```jldoctest
julia> using MIMEFileExtensions

julia> mimes_from_fileext("txt")
1-element Vector{Symbol}:
 Symbol("text/plain")
```
