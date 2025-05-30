```
find_min_covariate_adjustment(g, X, Y, I = Set{eltype(g)}(), R = setdiff(Set(vertices(g)), X, Y))
```

グラフ `g` における頂点の集合 `X` と `Y` に対して、$I ⊆ Z ⊆ R$ を満たす包含最小の共変量調整集合 `Z` を見つける。そうでない場合は `false` を返す。

https://arxiv.org/abs/1803.00116 で提案されたアルゴリズム的アプローチに基づいています。  
