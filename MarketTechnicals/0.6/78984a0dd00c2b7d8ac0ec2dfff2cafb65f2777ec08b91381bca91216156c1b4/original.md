```
donchianchannels(ohlc::TimeArray, n = 20; h = :High, l = :Low)
```

Donchian Channels

# Formula

$$
\begin{align*}
  \text{Up}   & = \max(P_1^\text{High}, \dots, P_t^\text{High}) \\
  \text{Mid}  & = \frac{\text{Up} + \text{Down}}{2} \\
  \text{Down} & = \min(P_1^\text{Low}, \dots, P_t^\text{Low})
\end{align*}
$$

# References

  * [TradingView Wiki](https://www.tradingview.com/wiki/Donchian_Channels_(DC))
