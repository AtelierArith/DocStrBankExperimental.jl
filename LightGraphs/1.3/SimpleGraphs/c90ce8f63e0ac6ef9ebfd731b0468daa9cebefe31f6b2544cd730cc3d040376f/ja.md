```
barabasi_albert!(g::AbstractGraph, n::Integer, k::Integer)
```

`n` 頂点を持つ [Barabási–Albert モデル](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model) のランダムグラフを作成します。これは、初期グラフ `g` に新しい頂点を追加することで成長します。各新しい頂点は、優先的接続によってシステム内に既に存在する `k` 個の異なる頂点に `k` 本のエッジで接続されます。

### オプション引数

  * `seed=-1`: RNG シードを設定します。

## 例

```jldoctest
julia> g = cycle_graph(4)
{4, 4} 無向単純 Int64 グラフ

julia> barabasi_albert!(g, 16, 3);

julia> g
{16, 40} 無向単純 Int64 グラフ
```
