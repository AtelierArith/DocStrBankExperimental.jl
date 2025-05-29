```
normalized_cut(g, thres, distmx=weights(g), [num_cuts=10]);
```

グラフに対して[再帰的二分正規化グラフカット](https://en.wikipedia.org/wiki/Segmentation-based_object_categorization#Normalized_cuts)を実行し、頂点を互いに排他的な集合に分割します。各頂点の集合インデックスを含むベクターを返します。

アプリケーションに適したしきい値を特定することが重要です。範囲(0,1)での二分探索が、しきい値の良い値を決定するのに役立ちます。

### キーワード引数

  * `thres`: 最良の正規化カットがこのしきい値を超える場合、部分グラフは分割されません
  * `num_cuts`: 最適なカットを決定するために実行されるカットの数

### 参考文献

"Normalized Cuts and Image Segmentation" - Jianbo Shi and Jitendra Malik
