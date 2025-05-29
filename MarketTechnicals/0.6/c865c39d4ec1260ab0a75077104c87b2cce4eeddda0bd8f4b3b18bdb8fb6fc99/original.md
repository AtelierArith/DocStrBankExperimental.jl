```
chaikinoscillator(ohlcv::TimeArray, fast = 3, slow = 10; h = :High, l = :Low, c = :Close)
```

Chaikin Oscillator

Developed by Marc Chaikin.

# Formula

$$
\text{Chaikin OSC} = \text{EMA}(\text{ADL}, \text{fast}) - \text{EMA}(\text{ADL}, \text{slow})
$$

where the [`adl`](@ref) is the Accumulation/Distribution Line.

# References

  * [StockCharts](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:chaikin_oscillator)
