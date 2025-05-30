```
find_min_backdoor_adjustment(g, X, Y, I = Set{eltype(g)}(), R = setdiff(Set(vertices(g)), X, Y))
```

グラフ `g` における頂点の集合 `X` と `Y` に対して、$I ⊆ Z ⊆ R$ を満たす包含最小のバックドア調整集合 `Z` を見つける。そうでなければ `false` を返す。

集合 X と Y への一般化は、例えば Pearl (2009) とは異なる。例のセクションを参照してください（TODO: ref）。
