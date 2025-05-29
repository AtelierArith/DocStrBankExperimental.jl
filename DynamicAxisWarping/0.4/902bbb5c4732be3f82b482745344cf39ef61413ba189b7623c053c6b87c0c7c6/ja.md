```
search_result = dtwnn(q, y, dist, rad, [normalizer::Type{Nothing}]; kwargs...)
```

`q`に対する`y`の最近傍を計算します。オプションの正規化タイプを指定できます。`ZNormalizer, DiagonalZNormalizer, NormNormalizer`を参照してください。

# 引数:

  * `q`: クエリ（短い時系列）
  * `y`: データ（長い時系列）
  * `dist`: 距離
  * `rad`: 半径
  * `showprogress`: デフォルトはtrue
  * `prune_endpoints = true`: エンドポイントヒューリスティックを使用
  * `prune_envelope  = true`: エンベロープヒューリスティックを使用
  * `bsf_multiplier  = 1`: 1より大きい場合、下限が`bsf_multiplier*best_so_far`を超える必要があります。
  * `saveall = false`: 密な結果を計算（時間がかかり、早期停止メソッドは使用されません）。falseの場合、距離の下限のベクトルが`search_result.dists`に保存されます。trueの場合、すべての距離が計算され保存されます。
  * `avoid`: 整数インデックス（またはインデックスのセット）が提供されると、このインデックスは検索で回避されます。これは、`q`が`y`の一部である場合に便利です。
