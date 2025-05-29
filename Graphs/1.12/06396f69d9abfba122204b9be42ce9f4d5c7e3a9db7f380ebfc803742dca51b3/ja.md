```
vertex_cover(g, RandomVertexCover(); rng=nothing, seed=nothing)
```

グラフ `g` のすべての辺が、少なくとも1つの端点としてこの集合に含まれるような頂点の集合を見つけます。

### 実装ノート

[近似最小頂点被覆](https://en.wikipedia.org/wiki/Vertex_cover#Approximate_evaluation)を1回実行します。頂点被覆に含まれる頂点を表すベクトルを返します。

### パフォーマンス

実行時間: O(|V|+|E|) メモリ: O(|E|) 近似係数: 2

### オプション引数

  * `rng=nothing`: ランダム数生成器を設定します。
  * `seed >= 0` の場合、この値でランダム生成器がシードされます。
