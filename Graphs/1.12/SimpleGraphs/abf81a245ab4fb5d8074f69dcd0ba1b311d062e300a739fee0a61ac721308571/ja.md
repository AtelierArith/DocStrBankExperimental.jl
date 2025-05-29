```
erdos_renyi(n, p::Real)
```

`n` 頂点を持つ [エルデシュ–レーニモデル](http://en.wikipedia.org/wiki/Erdős–Rényi_model) のランダムグラフを作成します。エッジは、確率 `p` で頂点のペア間に追加されます。

エルデシュ–レーニモデルには、確率 `p` ではなく、エッジの総数を一定に保つ別の定義が存在することに注意してください。この定義にアクセスするには、`erdos_renyi(n, ne::Integer)` を使用します（具体的には: `erdos_renyi(n, 1) != erdos_renyi(n, 1.0)`）。

### オプション引数

  * `is_directed=false`: true の場合、向き付きグラフを返します。
  * `rng=nothing`: ランダム数生成器を設定します。
  * `seed=nothing`: RNG シードを設定します。

# 例

```
julia> using Graphs

julia> erdos_renyi(10, 0.5)
{10, 20} 無向単純 Int64 グラフ
```

```
julia> using Graphs

julia> erdos_renyi(10, 0.5, is_directed=true, seed=123)
{10, 49} 有向単純 Int64 グラフ
```
