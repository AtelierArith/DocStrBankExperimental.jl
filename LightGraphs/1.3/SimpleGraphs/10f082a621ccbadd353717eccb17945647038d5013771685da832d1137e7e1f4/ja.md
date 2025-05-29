```
random_tournament_digraph(n)
```

`n` 頂点を持つランダムな有向 [トーナメントグラフ](https://en.wikipedia.org/wiki/Tournament_%28graph_theory%29) を作成します。

### オプション引数

  * `seed=-1`: RNG シードを設定します。

# 例

```jldoctest
julia> random_tournament_digraph(5)
{5, 10} 有向単純 Int64 グラフ

julia> random_tournament_digraph(Int8(10), seed=123)
{10, 45} 有向単純 Int8 グラフ
```
