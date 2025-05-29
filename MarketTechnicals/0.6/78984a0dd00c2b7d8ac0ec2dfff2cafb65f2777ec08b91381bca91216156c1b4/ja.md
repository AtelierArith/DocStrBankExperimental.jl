```
donchianchannels(ohlc::TimeArray, n = 20; h = :High, l = :Low)
```

ダンチアンチャネル

# 数式

$$
\begin{align*}
  \text{Up}   & = \max(P_1^\text{High}, \dots, P_t^\text{High}) \\
  \text{Mid}  & = \frac{\text{Up} + \text{Down}}{2} \\
  \text{Down} & = \min(P_1^\text{Low}, \dots, P_t^\text{Low})
\end{align*}
$$

# 参考文献

  * [TradingView Wiki](https://www.tradingview.com/wiki/Donchian_Channels_(DC))
