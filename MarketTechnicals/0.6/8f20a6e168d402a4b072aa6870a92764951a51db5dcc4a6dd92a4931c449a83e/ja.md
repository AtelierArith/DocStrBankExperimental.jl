```
keltnerbands(ohlc, n = 20, w = 2; h = :High, l = :Low, c = :Close)
```

ケルトナーチャネル

リンダ・ブラッドフォード・ラシュケは1980年代にケルトナーチャネルの新しいバージョンを紹介しました。私たちは新しいバージョンを実装します。

# 数式

$$
\begin{align*}
  \text{Up}   & = \text{Mid} + w \times \text{ATR}(n) \\
  \text{Mid}  & = \text{EMA}(P^{typical}, n) \\
  \text{Down} & = \text{Mid} - w \times \text{ATR}(n)
\end{align*}
$$

# 参考文献

  * [StockCharts](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:keltner_channels)
  * [Wikipedia](https://en.wikipedia.org/wiki/Keltner_channel)
