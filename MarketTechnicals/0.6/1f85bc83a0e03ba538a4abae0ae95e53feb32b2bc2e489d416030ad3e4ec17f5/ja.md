```
stochasticoscillator(ohlc, n = 14, fast_d = 3, slow_d = 3; h = :High, l = :Low, c = :Close)
```

ストキャスティックオシレーター

別名 *%K%D*、または *KD*

# 引数

  * `n`: ファスト（生）`%K`の期間
  * `fast_d`: ファスト`%D`のMA期間
  * `slow_d`: スロー`%D`のMA期間

# 公式

$$
\begin{align*}
  \text{fast %K} & = \frac{\text{Close}_t - \max(\text{High}_{t-n}, \dots, \text{High}_t)}
        {\max(\text{High}_{t-n}, \dots, \text{High}_t) - \min(\text{Low}_{t-n}, \dots, \text{Low}_t)}
        \times 100 \\
  \text{fast %D} & = \text{SMA}(\text{fast %K}) \\
  \text{slow %D} & = \text{SMA}(\text{fast %D})
\end{align*}
$$

# 参考文献

  * [Wikipedia](https://en.wikipedia.org/wiki/Stochastic_oscillator)
  * [FMLabs](http://www.fmlabs.com/reference/default.htm?url=StochasticOscillator.htm)
