```
threeletter(residue::String)
```

1文字のコードまたは残基名から3文字の天然アミノ酸残基コードを返す関数です。この関数は大文字と小文字を区別しません。

# 例

```julia-repl
julia> threeletter("A")
"ALA"

julia> threeletter("Aspartic acid")
"ASP"

julia> threeletter("HSD")
"HIS"
```
