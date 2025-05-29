```
chaikinoscillator(ohlcv::TimeArray, fast = 3, slow = 10; h = :High, l = :Low, c = :Close)
```

チャイキンオシレーター

マーク・チャイキンによって開発されました。

# 数式

$$
\text{Chaikin OSC} = \text{EMA}(\text{ADL}, \text{fast}) - \text{EMA}(\text{ADL}, \text{slow})
$$

ここで、[`adl`](@ref) は累積/分配ラインです。

# 参考文献

  * [StockCharts](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:chaikin_oscillator)
