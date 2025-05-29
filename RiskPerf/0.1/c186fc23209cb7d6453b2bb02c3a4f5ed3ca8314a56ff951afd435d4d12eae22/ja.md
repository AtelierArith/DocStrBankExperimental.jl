```
adjusted_sharpe_ratio(returns; multiplier=1.0, risk_free=0.0)
```

PezierとWhite（2006）によって導入された調整済みシャープレシオを計算し、負の歪度と過剰尖度にペナルティを課します。

# 数式

$$
\text{SR} = \dfrac{\mathbb{E}\left[ \text{returns} - \text{risk\_free}\right ]}{\sigma(\text{returns} - \text{risk\_free})}
$$

$$
\text{ASR} = \text{SR} \left[1 + \frac{S}{6}\text{SR} - \frac{K-3}{24}\text{SR}^2\right] \times \sqrt{\text{multiplier}}
$$

# 引数

  * `returns`:        資産のリターンのベクトル。
  * `multiplier`:     オプションのスカラー乗数、すなわち、月次リターンを年換算するには`12`を使用し、日次リターンを年換算するには`252`を使用します。
  * `risk_free`:      リスクフリーリターンを示すオプションのベクトルまたはスカラー値（提供されたリターンと同じ頻度である必要があります、例：日次）。

# 出典

  * Pezier, Jaques and White, Anthony (2006). The Relative Merits of Investable Hedge Fund Indices and of Funds of Hedge Funds in Optimal Passive Portfolios. ICMA Centre Discussion Papers in Finance.
