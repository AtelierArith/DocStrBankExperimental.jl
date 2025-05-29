```
erdos_renyi(GraphType, n, p)
```

`n` 頂点を持つ [エルデシュ–レーニモデル](http://en.wikipedia.org/wiki/Erdős–Rényi_model) のランダムグラフを作成します。エッジは、確率 `p` で頂点のペア間に追加されます。

### オプション引数

  * `seed=-1`: RNG シードを設定します。
  * `rng`: RNG を直接設定します。

### 参考文献

  * https://github.com/JuliaGraphs/LightGraphs.jl/blob/2a644c2b15b444e7f32f73021ec276aa9fc8ba30/src/SimpleGraphs/generators/randgraphs.jl
