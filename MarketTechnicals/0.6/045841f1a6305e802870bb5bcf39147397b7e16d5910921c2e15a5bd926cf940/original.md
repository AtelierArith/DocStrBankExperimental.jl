```
ultimateoscillator(ohlc::TimeArray, s = 7, m = 14, len = 28,
                   ws = 4.0, wm = 2.0, wl = 1.0;
                   c = :Close, h = :High, l = :Low)
```

Ultimate Oscillator

Larry Williams' (1976) signal, a momentum oscillator designed to capture momentum across three different timeframes.

$$
\begin{align*}
  \text{BP}        & = P^\text{Close} - \min(P^\text{Low}, P_{t-1}^\text{Close}) \\
  \text{TR}        & = \max(P^\text{High}, P_{t-1}^\text{Close}) -
                       \min(P^\text{Low},  P_{t-1}^\text{Close}) \\
  \text{Average7}  & = \frac{\text{7-period BP Sum}}{\text{7-period TR Sum}} \\
  \text{Average14} & = \frac{\text{14-period BP Sum}}{\text{14-period TR Sum}} \\
  \text{Average28} & = \frac{\text{28-period BP Sum}}{\text{28-period TR Sum}} \\
  \text{UO}        & = 100 \times
                       \frac{(4 \times \text{Average7}) +
                             (2 \times \text{Average14}) +
                             \text{Average28}}
                            {4 + 2 + 1}
\end{align*}
$$

# References

  * [StockCharts](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:ultimate_oscillator)
