```
find_min_frontdoor_adjustment(g, X, Y, I = Set{eltype(g)}(), R = setdiff(Set(vertices(g)), X, Y))
```

グラフ `g` における頂点の集合 `X` と `Y` に対して、$I ⊆ Z ⊆ R$ を満たす包含最小のフロントドア調整集合 `Z` を見つける。見つからない場合は `false` を返す。

https://arxiv.org/abs/2211.16468 に示されたアルゴリズムに基づく。
