```
awesomeoscillator(ohlc::TimeArray, s = 5, n = 34; h = :High, l = :Low)
```

Awesome Oscillator

The Awesome Oscillator is an indicator used to measure market momentum. AO calculates the difference of a 34 Period and 5 Period Simple Moving Averages. The Simple Moving Averages that are used are not calculated using closing price but rather each bar's midpoints. AO is generally used to affirm trends or to anticipate possible reversals [1].

Awesome Oscillator is a 34-period simple moving average, plotted through the central points of the bars (H+L)/2, and subtracted from the 5-period simple moving average, graphed across the central points of the bars $\frac{H + L}{2}$ [2].

$$
\begin{align*}
  \text{Median Price} & = \frac{P^\text{High} + P^\text{Low}}{2} \\
  \text{AO}           & = \text{SMA}(\text{Median Price}, 5) -
                          \text{SMA}(\text{Median Price}, 34)
\end{align*}
$$

# References

1. [TradingView](https://www.tradingview.com/wiki/Awesome_Oscillator_(AO))
2. https://www.ifcm.co.uk/ntx-indicators/awesome-oscillator
