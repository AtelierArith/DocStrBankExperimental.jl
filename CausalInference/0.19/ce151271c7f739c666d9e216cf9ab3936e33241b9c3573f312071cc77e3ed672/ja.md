```
list_backdoor_adjustment(g, X, Y, I = Set{eltype(g)}(), R = setdiff(Set(vertices(g)), X, Y))
```

グラフ `g` における頂点の集合 `X` と `Y` に対して、$I ⊆ Z ⊆ R$ を満たすすべてのバックドア調整セット `Z` をリストします。
