```
rename_edges!(D::DeltaComplex, p::Vector{<:Integer})
```

`D`内のすべてのエッジ(`DualEdge`)を、順列`p`に従って再ラベル付けします。

`DualEdge` 1 => `DualEdge` $p[1]$
