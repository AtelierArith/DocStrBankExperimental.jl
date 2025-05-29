```
adl(ohlcv; h = :High, l = :Low, c = :Close, v = :Volume)
```

累積/分配ライン

マーク・チャイキンによって開発されました。

# 数式

$$
ADL_t = ADL_{t-1} +
    'frac{(Close_t - Low_t) - (High_t - Close_t)}{High_t - Low_t}'
    'times Volume_t'
$$

# 参考文献

  * [StockCharts](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:accumulation_distribution_line)
