```
residuename(residue::Union{AbstractString,Char})
```

他の残基コードから長い残基名を返す関数です。この関数は大文字と小文字を区別しません。

### 例

```julia-repl
julia> residuename("A")
"Alanine"

julia> residuename("Glu")
"Glutamic Acid"

```
