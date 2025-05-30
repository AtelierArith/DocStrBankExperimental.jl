```
find_backdoor_adjustment(g, X, Y, I = Set{eltype(g)}(), R = setdiff(Set(vertices(g)), X, Y))
```

グラフ `g` における頂点の集合 `X` と `Y` に対して、$I ⊆ Z ⊆ R$ を満たすバックドア調整セット `Z` を見つける。見つからない場合は `false` を返す。

集合 X と Y への一般化は、例えば Pearl (2009) とは異なる。例のセクションを参照してください（TODO: ref）。
