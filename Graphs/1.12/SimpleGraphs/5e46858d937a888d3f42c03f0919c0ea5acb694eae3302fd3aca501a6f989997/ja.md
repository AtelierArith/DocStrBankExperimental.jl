```
watts_strogatz(n, k, β)
```

`n` 頂点を持つ [Watts-Strogatz](https://en.wikipedia.org/wiki/Watts_and_Strogatz_model) 小世界ランダムグラフを返します。各頂点は期待される次数 `k` （または `k` が奇数の場合は `k - 1`）を持ちます。エッジは確率 `β` に基づいてモデルに従ってランダム化されます。

アルゴリズムは次のように進行します。まず、各頂点が左右に正確に `div(k, 2)` の隣接頂点を持つ完全な1次元格子が構築されます（すなわち、合計で `k` または `k - 1`）。次に、ホップ長 `i` を `1` から `div(k, 2)` まで繰り返します。

1. 各頂点 `s` を順番に考慮し、その `i` 番目の最近接隣接頂点 `t` とのエッジを時計回りに考えます。
2. 一様にランダムな数 `r` を生成します。もし `r ≥ β` であれば、エッジ `(s, t)` は変更されません。そうでなければ、エッジは削除され、*再配線*されて `s` がグラフ全体から一様にランダムに選ばれた頂点 `d` に接続されます。ただし、`s` とその隣接頂点は除外されます。（`t` は有効な候補です。）

`β = 0` の場合、グラフは1次元格子のままとなり、`β = 1` の場合、すべてのエッジはランダムに再配線されます。

### オプション引数

  * `remove_edges=true`: false の場合、元のエッジを削除しません。
  * `is_directed=false`: true の場合、向き付きグラフを返します。
  * `rng=nothing`: ランダム数生成器を設定します。
  * `seed=nothing`: RNG シードを設定します。

## 例

```jldoctest
julia> using Graphs

julia> watts_strogatz(10, 4, 0.3)
{10, 20} 無向単純 Int64 グラフ

julia> watts_strogatz(Int8(10), 4, 0.8, is_directed=true, seed=123)
{10, 20} 有向単純 Int8 グラフ
```

### 参考文献

  * 「小世界」ネットワークの集合的ダイナミクス、ダンカン・J・ワッツ、スティーブン・H・ストロガッツ。 [https://doi.org/10.1038/30918](https://doi.org/10.1038/30918)
  * 小世界、ダンカン・J・ワッツ。 [https://en.wikipedia.org/wiki/Special:BookSources?isbn=978-0691005416](https://en.wikipedia.org/wiki/Special:BookSources?isbn=978-0691005416)

```
