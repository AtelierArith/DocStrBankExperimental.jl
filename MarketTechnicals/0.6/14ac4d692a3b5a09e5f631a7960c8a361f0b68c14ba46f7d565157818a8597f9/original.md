```
env(ta::TimeArray, n; e = 0.1)
env(A::AbstractArray, n; e = 0.1)
```

Moving Average Envelope

$$
\begin{align*}
  \text{Upper Envelope} & = \text{SMA}(n) \times (1 + e) \\
  \text{Lower Envelope} & = \text{SMA}(n) \times (1 - e)
\end{align*}
$$

# Arguments

  * `e`: the envelope, `0.1` implies the `10%` envelope.

# References

  * [TradingView](https://www.tradingview.com/wiki/Envelope_(ENV))
