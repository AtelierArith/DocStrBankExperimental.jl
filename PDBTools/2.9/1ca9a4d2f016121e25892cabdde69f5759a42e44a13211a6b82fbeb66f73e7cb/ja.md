```
oneletter(residue::Union{AbstractString,Char})
```

三文字コードまたは残基名から一文字の残基コードを返す関数です。この関数は大文字と小文字を区別しません。

### 例

```julia-repl
julia> oneletter("ALA")
"A"

julia> oneletter("Glutamic acid")
"E"

```
