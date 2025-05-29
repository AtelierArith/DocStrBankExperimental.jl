```
watts_strogatz(n, k, β)
```

`n` 頂点を持ち、各頂点の次数が `k` の [Watts-Strogatz](https://en.wikipedia.org/wiki/Watts_and_Strogatz_model) 小モデルランダムグラフを返します。エッジは確率 `β` に基づいてモデルに従ってランダム化されます。

### オプション引数

  * `is_directed=false`: true の場合、向き付きグラフを返します。
  * `seed=-1`: RNG シードを設定します。

## 例

```jldoctest
julia> watts_strogatz(10, 4, 0.3)
{10, 20} 無向単純 Int64 グラフ

julia> watts_strogatz(Int8(10), 4, 0.8, is_directed=true, seed=123)
{10, 20} 有向単純 Int8 グラフ
```
