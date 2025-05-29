```
hsp_queries(dist, X::AbstractDatabase, Q::AbstractDatabase, knns, dists; <kwargs>)
hsp_queries(dist, X::AbstractDatabase, Q::AbstractDatabase, k::Integer; <kwargs>)
hsp_queries(idx::AbstractSearchIndex, Q::AbstractDatabase, k::Integer; <kwargs>)
```

クエリ `Q` のハーフスペースパーティションを計算します（`knns`、`dists` として与えられる可能性があります）

## オプションのキーワード引数

  * `ctx::SearchGraphContext` 検索コンテキスト（キャッシュ）
  * `minbatch::Int`: マルチスレッドの実行を制御する `Polyester.@batch` パラメータ
