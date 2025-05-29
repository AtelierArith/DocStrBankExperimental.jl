```
erdos_renyi(n, ne)
```

`n` 頂点と `ne` 辺を持つ [エルデシュ–レーニモデル](http://en.wikipedia.org/wiki/Erdős–Rényi_model) のランダムグラフを作成します。

### オプション引数

  * `is_directed=false`: true の場合、向き付きグラフを返します。
  * `seed=-1`: RNG シードを設定します。

# 例

```jldoctest
julia> erdos_renyi(10, 30)
{10, 30} 無向単純 Int64 グラフ

julia> erdos_renyi(10, 30, is_directed=true, seed=123)
{10, 30} 有向単純 Int64 グラフ
```
