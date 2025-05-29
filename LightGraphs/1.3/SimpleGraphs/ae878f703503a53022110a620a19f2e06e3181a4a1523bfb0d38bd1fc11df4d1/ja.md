```
erdos_renyi(n, p)
```

`n` 頂点を持つ [エルデシュ–レーニモデル](http://en.wikipedia.org/wiki/Erdős–Rényi_model) のランダムグラフを作成します。エッジは、確率 `p` で頂点のペア間に追加されます。

### オプション引数

  * `is_directed=false`: true の場合、向き付きグラフを返します。
  * `seed=-1`: RNG シードを設定します。

# 例

```jldoctest
julia> erdos_renyi(10, 0.5)
{10, 20} 無向単純 Int64 グラフ

julia> erdos_renyi(10, 0.5, is_directed=true, seed=123)
{10, 49} 有向単純 Int64 グラフ
```
