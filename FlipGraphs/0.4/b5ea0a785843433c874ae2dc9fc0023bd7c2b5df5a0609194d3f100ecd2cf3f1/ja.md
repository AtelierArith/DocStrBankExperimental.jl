```
rename_vertices!(D::DeltaComplex, p::Vector{<:Integer})
```

`D`内のすべての頂点(`TriFace`)を、置換`p`に従って再ラベル付けします。

`TriFace` 1 => `TriFace` $p[1]$ 
