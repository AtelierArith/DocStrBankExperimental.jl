```
random_regular_digraph(n, k)
```

`n` 頂点を持ち、各頂点の次数が `k` であるランダムな有向 [正則グラフ](https://en.wikipedia.org/wiki/Regular_graph) を作成します。

### オプション引数

  * `dir=:out`: 次数パラメータのための辺の方向。
  * `rng=nothing`: ランダム数生成器を設定します。
  * `seed=nothing`: RNG シードを設定します。

### 実装ノート

ブールの疎行列としての隣接行列を $n × n$ アロケートし、それを使用して有向グラフを生成します。 ```
