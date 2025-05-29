```
label_propagation(g; maxiter=1000)
```

ラベル伝播アルゴリズムを使用したコミュニティ検出（[Raghavan et al.](http://arxiv.org/abs/0709.2938)を参照）。`g`は入力グラフで、`maxiter`は最大反復回数です。頂点の割り当てと収束履歴を返します。
