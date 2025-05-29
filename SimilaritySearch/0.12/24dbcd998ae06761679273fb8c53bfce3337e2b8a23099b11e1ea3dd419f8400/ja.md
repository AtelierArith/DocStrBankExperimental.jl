```
searchbatch(index, ctx, Q, k::Integer) -> indices, distances
searchbatch(index, Q, k::Integer) -> indices, distances
```

指定されたインデックス内でクエリのバッチを検索します（k近傍を検索します）。

# 引数

  * `index`: 検索構造
  * `Q`: クエリのセット
  * `k`: 取得する近傍の数
  * `context`: キャッシュ、ハイパーパラメータ、およびメタデータ（デフォルトは `getcontext(index)`）

注意: indices と distances の i 番目の列は `Q` の i 番目のクエリに対応します 注意: 各列の最終的な indices は、検索プロセスが `k` 近傍を取得できなかった場合、`0` になることがあります。
