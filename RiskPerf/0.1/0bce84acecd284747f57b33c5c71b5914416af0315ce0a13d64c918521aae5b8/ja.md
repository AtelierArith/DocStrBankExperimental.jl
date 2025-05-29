```
treynor_ratio(asset_returns, benchmark_returns; multiplier=1.0, risk_free=0.0)
```

超過リターンをCAPMベータで割った比率としてトレイナー比率を計算します。この比率はシャープ比率に似ていますが、ボラティリティで割る代わりにリスクの代理としてCAPMベータで割ります。

# 公式

$$
\text{TR} = \dfrac{ \mathbb{E}\left[ \text{asset\_returns} - \text{risk\_free} \right]}{\beta} \times \text{multiplier}
$$

# 引数

  * `asset_returns`:      資産リターンのベクトル。
  * `benchmark_returns`:  ベンチマークリターンのベクトル（例：市場ポートフォリオリターン）。
  * `multiplier`:         オプションのスカラー乗数。すなわち、月次リターンを年換算するには`12`を使用し、日次リターンを年換算するには`252`を使用します。
  * `risk_free`:          リスクフリーリターンを示すオプションのベクトルまたはスカラー値（提供されたリターンと同じ頻度である必要があります、例：日次）。
