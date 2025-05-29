```
adl(ohlcv; h = :High, l = :Low, c = :Close, v = :Volume)
```

Accumulation/Distribution Line

Developed by Marc Chaikin.

# Formula

$$
ADL_t = ADL_{t-1} +
    'frac{(Close_t - Low_t) - (High_t - Close_t)}{High_t - Low_t}'
    'times Volume_t'
$$

# References

  * [StockCharts](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:accumulation_distribution_line)
