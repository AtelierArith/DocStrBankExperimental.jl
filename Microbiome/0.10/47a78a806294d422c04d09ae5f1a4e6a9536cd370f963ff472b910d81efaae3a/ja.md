```
taxon(::AbstractString)
```

文字列表現から[`Taxon`](@ref)を返します。文字列に`"x__Thename"`の形式で分類階級情報が含まれている場合、ここで`x`は階級の最初の文字であり、この情報が使用されます。

## 例

```julia-repl
julia> taxon("Unknown")
Taxon("Unknown", missing)

julia> taxon("s__Prevotella_copri")
Taxon("Prevotella_copri", :species)
```
