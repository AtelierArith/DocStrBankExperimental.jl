```
env(ta::TimeArray, n; e = 0.1)
env(A::AbstractArray, n; e = 0.1)
```

移動平均エンベロープ

$$
\begin{align*}
  \text{上部エンベロープ} & = \text{SMA}(n) \times (1 + e) \\
  \text{下部エンベロープ} & = \text{SMA}(n) \times (1 - e)
\end{align*}
$$

# 引数

  * `e`: エンベロープ、`0.1`は`10%`のエンベロープを意味します。

# 参考文献

  * [TradingView](https://www.tradingview.com/wiki/Envelope_(ENV))
