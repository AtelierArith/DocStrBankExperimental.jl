```
community_detection_bethe(g::AGraph, k=-1; kmax=15)
```

`g`に関連するベッテヘッシアン行列のスペクトル特性を使用したコミュニティ検出（[Saade et al.](http://papers.nips.cc/paper/5520-spectral-clustering-of-graphs-with-the-bethe-hessian)を参照）。`k`は検出するコミュニティの数です。省略するか、`k < 1`の場合、最適なコミュニティの数が自動的に選択されます。この場合、検出可能なコミュニティの最大数は`kmax`で与えられます。頂点の割り当てを含むベクターを返します。
