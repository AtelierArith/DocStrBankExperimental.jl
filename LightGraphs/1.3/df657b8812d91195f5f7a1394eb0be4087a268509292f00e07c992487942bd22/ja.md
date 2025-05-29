```
vertex_cover(g, RandomVertexCover(); seed=-1)
```

グラフ `g` のすべての辺が、セット内の少なくとも1つの端点としての頂点を持つような頂点の集合を見つけます。

### 実装ノート

[近似最小頂点被覆](https://en.wikipedia.org/wiki/Vertex_cover#Approximate_evaluation)を1回実行します。頂点被覆内の頂点を表すベクトルを返します。

### パフォーマンス

実行時間: O(|V|+|E|) メモリ: O(|E|) 近似係数: 2

### オプション引数

  * `seed >= 0` の場合、この値で乱数生成器がシードされます。
