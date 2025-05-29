```
expected_degree_graph(ω)
```

与えられたベクトルの期待度 `ω` に基づいて、頂点 `i` と `j` が確率 `ω[i]*ω[j]/sum(ω)` で接続されるランダム無向グラフを作成します。

### オプション引数

  * `rng=nothing`: ランダム数生成器を設定します。
  * `seed=nothing`: RNGシードを設定します。

### 実装ノート

アルゴリズムは `maximum(ω) << sum(ω)` の場合にうまく機能するはずです。`maximum(ω)` が `sum(ω)` に近づくにつれて、期待値からのいくつかの偏差が発生する可能性があります。

### 参考文献

  * 期待度列が与えられたランダムグラフにおける連結成分、Linyuan Lu と Fan Chung. [https://link.springer.com/article/10.1007%2FPL00012580](https://link.springer.com/article/10.1007%2FPL00012580)
  * 与えられた期待度を持つネットワークの効率的生成、Joel C. Miller と Aric Hagberg. [https://doi.org/10.1007/978-3-642-21286-4_10](https://doi.org/10.1007/978-3-642-21286-4_10)

# 例

```
# 1)
julia> using Graphs

julia> g = expected_degree_graph([3, 1//2, 1//2, 1//2, 1//2])
{5, 3} undirected simple Int64 graph

julia> print(degree(g))
[3, 0, 1, 1, 1]

# 2)
julia> g = expected_degree_graph([0.5, 0.5, 0.5], seed=123)
{3, 1} undirected simple Int64 graph

julia> print(degree(g))
[1, 0, 1]
```
