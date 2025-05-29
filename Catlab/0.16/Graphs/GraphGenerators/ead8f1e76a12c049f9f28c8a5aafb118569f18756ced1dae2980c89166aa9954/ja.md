```
watts_strogatz(n, k, β)
```

`n` 頂点を持つ [Watts-Strogatz](https://en.wikipedia.org/wiki/Watts_and_Strogatz_model) 小世界ランダムグラフを返します。各頂点は期待度数 `k` (または `k` が奇数の場合は `k * 1`) を持ちます。エッジは確率 `β` に基づいてモデルに従ってランダム化されます。

アルゴリズムは次のように進行します。まず、各頂点が正確に `div(k, 2)` の隣接点を持つ完全な 1-格子が構築されます (すなわち、合計で `k` または `k - 1`)。次に、以下のステップが `i` のホップ長を `1` から `div(k, 2)` まで繰り返されます。

1. 各頂点 `s` を順番に考慮し、その `i` 番目の最近接隣接点 `t` とのエッジを時計回りに見ます。
2. 一様にランダムな数 `r` を生成します。もし `r ≥ β` であれば、エッジ `(s, t)` は変更されずに残ります。そうでなければ、エッジは削除され、*再配線*されて `s` がグラフ全体から一様にランダムに選ばれた頂点 `d` に接続されます。ただし、`s` とその隣接点は除外されます。(注意: `t` は有効な候補です。)

`β = 0` の場合、グラフは 1-格子のままとなり、`β = 1` の場合、すべてのエッジはランダムに再配線されます。

### オプション引数

  * `is_directed=false`: true の場合、向き付きグラフを返します。
  * `seed=-1`: RNG シードを設定します。

### 参考文献

  * Collective dynamics of ‘small-world’ networks, Duncan J. Watts, Steven H. Strogatz. [https://doi.org/10.1038/30918](https://doi.org/10.1038/30918)
  * Small Worlds, Duncan J. watts. [https://en.wikipedia.org/wiki/Special:BookSources?isbn=978-0691005416](https://en.wikipedia.org/wiki/Special:BookSources?isbn=978-0691005416)
  * https://github.com/JuliaGraphs/LightGraphs.jl/blob/2a644c2b15b444e7f32f73021ec276aa9fc8ba30/src/SimpleGraphs/generators/randgraphs.jl#L187

```
