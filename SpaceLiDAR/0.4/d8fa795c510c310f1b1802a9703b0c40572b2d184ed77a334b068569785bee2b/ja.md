```
instantiate(granules::Vector{::Granule}, folder::AbstractString)
```

与えられた `granules` のリストから [`find`](@ref) を使用して、グラニュールをローカルファイルにマッチさせ、存在する場合はローカルファイルパスを持つ新しいグラニュールのリストを返します。
