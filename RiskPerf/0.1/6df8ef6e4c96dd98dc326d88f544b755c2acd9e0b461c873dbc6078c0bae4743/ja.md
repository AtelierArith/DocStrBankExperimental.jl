```
sharpe_ratio(returns; multiplier=1.0, risk_free=0.0)
```

ウィリアム・F・シャープによる1966年の元の定義に従ってシャープレシオ（SR）を計算します。1994年のシャープの改訂に従ってシャープレシオを計算するには、関数`information_ratio`（IR）を参照してください。

# 数式

$$
\text{SR} = \dfrac{\mathbb{E}\left[\text{returns} - \text{risk\_free} \right]}{\sigma(\text{returns})} \times \sqrt{\text{multiplier}}
$$

$$
\text{IR} = \dfrac{\mathbb{E}\left[\text{asset\_returns} - \text{benchmark\_returns} \right]}{\sigma(\text{asset\_returns} - \text{benchmark\_returns})} \times \sqrt{\text{multiplier}}
$$

# 引数

  * `returns`:        資産のリターンのベクトル。
  * `multiplier`:     オプションのスカラー乗数。たとえば、月次リターンを年換算するには`12`を使用し、日次リターンを年換算するには`252`を使用します。
  * `risk_free`:      リスクフリーリターンを示すオプションのベクトルまたはスカラー値（提供されたリターンと同じ頻度である必要があります。例：日次）。

# 出典

  * Sharpe, W. F. (1966). Mutual Fund Performance. Journal of Business.
  * Sharpe, William F. (1994). The Sharpe Ratio. The Journal of Portfolio Management.
