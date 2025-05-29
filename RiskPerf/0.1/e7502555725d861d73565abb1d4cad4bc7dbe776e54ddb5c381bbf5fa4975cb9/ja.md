```
modified_jensen(asset_returns, benchmark_returns; risk_free=0.0)
```

ジェンセンのアルファを系統的リスクで割り、系統的リスクあたりの系統的リスク調整後のリターンを測定します。`jensen_alpha`も参照してください。

# 引数

  * `asset_returns`:      資産リターンのベクトル。
  * `benchmark_returns`:  ベンチマークリターンのベクトル（例：CAPMベータのための市場ポートフォリオリターン）。
  * `risk_free`:          提供されたリターンと同じ頻度を持つリスクフリーリターンを示すオプションのベクトルまたはスカラー値（例：日次）。

# 戻り値

修正されたジェンセンのアルファ測定値。

# 出典

  * Bacon, Carl (2008). Practical Portfolio Performance Measurement and Attribution, 2nd Edition, John Wiley & Sons Ltd. Page 77.
