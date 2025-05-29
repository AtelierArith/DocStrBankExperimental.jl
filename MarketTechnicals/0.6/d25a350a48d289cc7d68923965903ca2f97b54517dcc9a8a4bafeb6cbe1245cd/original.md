```
williamsr(ohlc::TimeArray, n = 14; c = :Close, h = :High, l = :Low)
```

Williams %R

Developed by Larry Williams, Williams %R is a momentum indicator that is the inverse of the Fast Stochastic Oscillator. Also referred to as %R, Williams %R reflects the level of the close relative to the highest high for the look-back period. In contrast, the Stochastic Oscillator reflects the level of the close relative to the lowest low. %R corrects for the inversion by multiplying the raw value by -100. As a result, the Fast Stochastic Oscillator and Williams %R produce the exact same lines, only the scaling is different. Williams %R oscillates from 0 to -100 [1].

Readings from 0 to -20 are considered overbought. Readings from -80 to -100 are considered oversold.

Unsurprisingly, signals derived from the Stochastic Oscillator are also applicable to Williams %R.

$$
\text{%R} = \frac{\text{Highest High} - P^\text{Close}}
                 {\text{Highest High} - \text{Lowest Low}}
                 \times -100
$$

Lowest Low = lowest low for the look-back period.

Highest High = highest high for the look-back period.

%R is multiplied by -100 correct the inversion and move the decimal.

The Williams %R oscillates from 0 to -100. When the indicator produces readings from 0 to -20, this indicates overbought market conditions. When readings are -80 to -100, it indicates oversold market conditions [2].

# References

1. [StockCharts](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:williams_r)
2. [Investopedia](https://www.investopedia.com/terms/w/williamsr.asp)
