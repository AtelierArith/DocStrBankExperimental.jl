```
barabasi_albert(n, k)
```

`n` 頂点を持つ [Barabási–Albert モデル](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model) のランダムグラフを作成します。これは、`k` 頂点を持つ初期グラフに新しい頂点を追加することで成長します。各新しい頂点は、優先的接続によってシステム内に既に存在する `k` の異なる頂点に `k` 本のエッジで接続されます。初期グラフは無向であり、デフォルトでは孤立した頂点で構成されています。

### オプション引数

  * `is_directed=false`: true の場合、向きのあるグラフを返します。
  * `complete=false`: true の場合、初期グラフに完全グラフを使用します。
  * `seed=-1`: RNG シードを設定します。

## 例

```jldoctest
julia> barabasi_albert(50, 3)
{50, 141} 無向単純 Int64 グラフ

julia> barabasi_albert(100, Int8(10), is_directed=true, complete=true, seed=123)
{100, 990} 有向単純 Int8 グラフ
```
