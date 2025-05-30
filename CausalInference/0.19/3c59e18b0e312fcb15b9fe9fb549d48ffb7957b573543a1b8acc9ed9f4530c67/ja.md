```
find_dsep(g, X, Y, I = Set{eltype(g)}(), R = setdiff(Set(vertices(g)), X, Y), veto = no_veto)
```

グラフ `g` における頂点の集合 `X` と `Y` に対して、$I ⊆ Z ⊆ R$ を満たす d-セパレーター `Z` を見つける。見つからない場合は `false` を返す。

https://arxiv.org/abs/1803.00116 で提案されたアルゴリズム的アプローチに基づく。
