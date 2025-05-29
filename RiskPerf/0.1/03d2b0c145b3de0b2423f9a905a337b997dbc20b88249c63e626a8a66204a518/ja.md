```
tracking_error(asset_returns, benchmark_returns; multiplier=1.0)
```

アクティブリターンの標準偏差に基づいて、事後トラッキングエラーを計算します。

# 公式

$$
\text{TE} = \sigma\left( \text{asset\_returns} - \text{benchmark\_returns} \right) \times \sqrt{\text{multiplier}}
$$

# 引数

  * `asset_returns`:      資産リターンのベクトル。
  * `benchmark_returns`:  ベンチマークリターンのベクトル。
  * `multiplier`:         オプションのスカラー乗数。すなわち、月次リターンを年換算するには `12` を使用し、日次リターンを年換算するには `252` を使用します。
