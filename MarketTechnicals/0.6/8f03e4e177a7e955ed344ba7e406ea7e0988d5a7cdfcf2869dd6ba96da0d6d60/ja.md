```
aroon(ohlc::TimeArray, n = 25; h = :High, l = :Low)
```

アroonオシレーター

# 数式

$$
\begin{align*}
  \text{up}   & = \frac{\mathop{argmax}(\text{High}_{t-n} \dots \text{High}_t)}{n} \times 100 \\
  \text{down} & = \frac{\mathop{argmin}(\text{Low}_{t-n} \dots \text{Low}_t)}{n} \times 100 \\
  \text{osc}  & = \text{up} - \text{down}
\end{align*}
$$

# 参考文献

  * [StockCharts](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:aroon_oscillator)
