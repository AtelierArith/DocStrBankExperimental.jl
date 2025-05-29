```
resname(residue::Union{AbstractString,Char})
```

与えられた1文字コードまたは残基名に基づいて残基名を返します。`threeletter`とは異なり、この関数は、タンパク質残基のリストに利用可能な場合、力場名を返します。

# 例

```julia-repl
julia> resname("ALA")
"ALA"

julia> resname("GLUP")
"GLUP"
```
