```
keltnerbands(ohlc, n = 20, w = 2; h = :High, l = :Low, c = :Close)
```

Keltner Channels

Linda Bradford Raschke introduced the newer version of Keltner Channels in the 1980s. We implement the newer version.

# Formula

$$
\begin{align*}
  \text{Up}   & = \text{Mid} + w \times \text{ATR}(n) \\
  \text{Mid}  & = \text{EMA}(P^{typical}, n) \\
  \text{Down} & = \text{Mid} - w \times \text{ATR}(n)
\end{align*}
$$

# References

  * [StockCharts](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:keltner_channels)
  * [Wikipedia](https://en.wikipedia.org/wiki/Keltner_channel)
