```
sortino_ratio(returns; multiplier=1.0, risk_free=0.0)
```

Sortino比率を計算します。これは、下方リスク調整されたパフォーマンス指標です。シャープ比率とは異なり、リスクの計算には最小許容リターンを下回る偏差のみが含まれます（標準偏差ではなく下方偏差）。

# 引数

  * `returns`:        資産リターンのベクトル。
  * `multiplier`:     オプションのスカラー乗数。例えば、月次リターンを年換算するには`12`を使用し、日次リターンを年換算するには`252`を使用します。
  * `MAR`:            最小許容リターンを示すオプションのベクトルまたはスカラー値。提供されたリターンと同じ頻度でなければなりません（例：日次）。

# 公式

$$
\text{Sortino Ratio} = \dfrac{\text{returns} - \text{MAR}}{\text{downside deviation}} \times \sqrt{\text{multiplier}}
$$

下方偏差は、最小許容リターンを下回るリターンの標準偏差に過ぎません。

# 出典

  * Sortino, F. and Price, L. (1996). Performance Measurement in a Downside Risk Framework. Journal of Investing.
