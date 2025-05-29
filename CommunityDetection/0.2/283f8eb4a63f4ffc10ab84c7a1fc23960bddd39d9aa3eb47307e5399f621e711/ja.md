```
community_detection_bethe(g::AbstractGraph, k=-1; kmax=15)
```

グラフ `g` に関連するベッテ・ヘッシアン行列のスペクトル特性を使用して、`k` コミュニティの検出を行います。`k` が省略されるか `1` 未満の場合、最適なコミュニティ数が自動的に選択されます。この場合、検出可能なコミュニティの最大数は `kmax` で与えられます。頂点の割り当てを含むベクトルを返します。

### 参考文献

  * [Saade et al.](http://papers.nips.cc/paper/5520-spectral-clustering-of-graphs-with-the-bethe-hessian)
