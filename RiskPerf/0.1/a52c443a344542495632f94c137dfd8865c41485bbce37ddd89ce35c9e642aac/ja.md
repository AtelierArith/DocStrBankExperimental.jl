```
jensen_alpha(asset_returns, benchmark_returns; risk_free=0.0)
```

ジェンセンのアルファ、または単にアルファは、リスク調整された超過パフォーマンスの指標です。これは、資本資産価格モデル（CAPM）によって予測されたものを上回るか下回るかの投資の平均リターンを示します。この指標は、投資とベンチマークのリスクが同一であるように超過リターンを調整します。

# 引数

  * `asset_returns`:      資産リターンのベクトル。
  * `benchmark_returns`:  ベンチマークリターンのベクトル（例：CAPMベータのための市場ポートフォリオリターン）。
  * `risk_free`:          オプションのベクトルまたはスカラー値で、リスクフリーリターンを示します（提供されたリターンと同じ頻度である必要があります、例：日次）。

# 戻り値

ジェンセンのアルファ指標。

# 出典

  * Bacon, Carl (2008). Practical Portfolio Performance Measurement and Attribution, 2nd Edition, John Wiley & Sons Ltd. Page 72.
